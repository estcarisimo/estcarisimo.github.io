# 1. Configuration
SAMPLE_RATE  = 16000   # YAMNet expects 16 kHz mono
# YAMNet expects exactly 15 600 samples (0.975 s at 16 kHz) per inference window
SAMPLES_PER_WINDOW = 15600
WINDOW_SEC   = SAMPLES_PER_WINDOW / SAMPLE_RATE  # ≈0.975 s

# 3. Audio capture thread
stream = sd.InputStream(
    samplerate=SAMPLE_RATE,
    device=DEVICE,
    channels=CHANNELS,
    blocksize=SAMPLES_PER_WINDOW,
    callback=audio_callback,
)

# 4. Main detection loop
def detect_loop():
    while True:
        chunk = q.get()
        mono  = np.squeeze(chunk).astype(np.float32)
        # Ensure the tensor has exactly 15 600 samples as YAMNet requires
        if mono.shape[0] != SAMPLES_PER_WINDOW:
            if mono.shape[0] > SAMPLES_PER_WINDOW:
                mono = mono[:SAMPLES_PER_WINDOW]
            else:  # pad with zeros if microphone underruns
                mono = np.pad(mono, (0, SAMPLES_PER_WINDOW - mono.shape[0]), mode='constant')

        interpreter.set_tensor(input_details[0]['index'], np.expand_dims(mono, axis=0))  # Provide correctly sized vector to model
        interpreter.invoke()
        output = interpreter.get_tensor(output_details[0]['index'])
        ...
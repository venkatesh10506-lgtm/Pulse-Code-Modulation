# Pulse-Code-Modulation
# Aim
Write a simple Python program for the modulation and demodulation of PCM, and DM.
# Tools required
Google colab
# Theory 
Pulse Code Modulation (PCM) is a technique used to convert an analog signal into a digital signal. It involves three steps: sampling, quantization, and encoding to produce a binary sequence. At the receiver, the signal is decoded and reconstructed to obtain the original analog signal
# Program
```
import numpy as np
import matplotlib.pyplot as plt

# Signal parameters
fs, f, T = 5000, 20, 0.5
t = np.arange(0, T, 1/fs)
msg = np.sin(2*np.pi*f*t)

# -------- Clock Signal --------
clk = np.sign(np.sin(2*np.pi*100*t))=

# -------- PCM --------
L = 16
step = (msg.max()-msg.min())/L
pcm = np.round(msg/step)*step
pcm_demod = pcm  # Ideal reconstruction

# -------- Delta Modulation --------
delta = 0.05
dm = [0]
steps = []

for s in msg:
    step = delta if s > dm[-1] else -delta
    steps.append(step)
    dm.append(dm[-1] + step)

dm_demod = np.cumsum([0] + steps)

# -------- Plot --------
plt.figure(figsize=(10,10))

plt.subplot(611); plt.plot(t,msg); plt.title("Analog Signal"); plt.grid()
plt.subplot(612); plt.plot(t,clk); plt.title("Clock Signal"); plt.grid()
plt.subplot(613); plt.step(t,pcm); plt.title("PCM Signal"); plt.grid()
plt.subplot(614); plt.plot(t,pcm_demod,'r--'); plt.title("PCM Demodulated"); plt.grid()
plt.subplot(615); plt.step(t,dm[:-1]); plt.title("Delta Modulation"); plt.grid()
plt.subplot(616); plt.plot(t,dm_demod[:-1],'g--'); plt.title("DM Demodulation"); plt.grid()

plt.tight_layout()
plt.show()
```
# Output Waveform
<img width="1241" height="411" alt="image" src="https://github.com/user-attachments/assets/dd27f85d-3d3e-44a3-8bbd-59b62fecca25" />
<img width="1238" height="417" alt="image" src="https://github.com/user-attachments/assets/e57bf819-1fcc-4f08-ba90-bd3d079f3813" />
<img width="1237" height="421" alt="image" src="https://github.com/user-attachments/assets/8490b35a-ed20-4265-9fc9-01d5796c3f54" />

# Results
Thus,the Pulse code modulation and demodulation is verified succesfully

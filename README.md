# lfm-sims
Preliminary Linear Frequency Modulation (LFM) radar simulations for the Topside Ionosonde Receiver Instrument (TIRI) on the MBHS Magnet3Sat mission

This project was inspired by https://github.com/rytse/tiri_tutorial/ by Ryan Tse.
This repository simulates LFM (linear frequency-modulated) radar signal propagation and reflection through the ionosphere under various geometries: vertical, ground-based oblique, and airborne oblique. The simulations model ionospheric radar measurements relevant to real-world CubeSat and ionosonde applications.

## Signal Processing Background

Each simulation uses an LFM chirp transmitted from a radar system. The received signal is a delayed version of the original, reflected from a virtual ionospheric height. By multiplying the transmitted signal with the complex conjugate of the received signal, we isolate a sinusoid whose frequency is proportional to the time delay. Using FFT, we extract this frequency to compute the reflection delay `τ` and back-calculate signal path length and virtual height.

---

## Notebooks

### `vertical.ipynb`
Simulates vertical ionosonde sounding from a stationary transmitter/receiver. The system sends an LFM chirp directly upward and receives the reflection from an assumed ionospheric height. The delay is used to estimate total flight distance and reflection altitude.

### `oblique_ground.ipynb`
Models an oblique one-way transmission between two ground-based stations. The notebook estimates virtual reflection height from known receiver separation and extracted signal delay, assuming a flat Earth and symmetric path.

### `oblique_airborne.ipynb`
Simulates an oblique radar reflection from a ground transmitter to an airborne receiver (e.g., CubeSat). It calculates the signal path length and reflection angle, estimating the ionospheric reflection altitude from geometric parameters and delay.

---

## Technologies Used

- Python 3.10+
- NumPy
- SciPy
- Matplotlib
- Jupyter Notebook

---

## How to Run

1. Clone the repo:
   ```bash
   git clone https://github.com/mbhs-tiri/lfm-sims.git
   cd lfm-sims```
2. Open the notebooks in Jupyter:
    ```bash
    jupyter notebook```
3. Run each cell in any of the `.ipynb` files.

## Output
Each notebook outputs:
- FFT spectrum showing beat frequency between TX and RX
- Estimated signal delay and virtual reflection height

## Applications
This simulation framework supports the development of ionospheric sounding systems, including preflight modeling for nanosatellite missions (e.g., CubeSat-based ionosondes) and ground-based radar experiments.

## 🔬 License & Authors
Developed by Eric Zou and the TIRI team at Montgomery Blair High School.
Licensed under the MIT License.

# EKF Localization Visualization

## Overview
This project implements a visualization for an **Extended Kalman Filter (EKF) localization** system. The EKF estimates the trajectory of a moving agent (e.g., robot or vehicle) based on sensor measurements and landmarks in a 2D environment. 

The Python script generates a comparative plot showing:
- **Landmarks**: Static reference points (▲ red)
- **Estimated Trajectory**: EKF-predicted path (● green)
- **Ground Truth**: Actual path (-- blue)

![Sample Visualization](https://github.com/user-attachments/assets/67dc620b-b42c-4ac3-9706-71a455226da3)  
*(Replace with actual screenshot)*

## Prerequisites
- **Python**: 3.10+
- **Dependencies**:
  ```bash
  matplotlib numpy seaborn
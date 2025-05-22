
EKF Localization Visualization

Overview
This project implements a visualization for an Extended Kalman Filter (EKF) localization system. The EKF is used to estimate the trajectory of a moving agent (e.g., a robot or vehicle) based on sensor measurements and landmarks in a 2D environment. The provided Python script generates a plot comparing:

Landmarks: Static reference points in the environment.
Estimated Trajectory: The agent's path as predicted by the EKF.
Ground Truth: The actual path of the agent for comparison.

The visualization uses Matplotlib to display the results, helping users analyze the accuracy of the EKF localization algorithm.
Prerequisites
To run the visualization, ensure you have the following installed:

Python: Version 3.10 or higher
Dependencies:
matplotlib: For plotting the visualization
numpy: For handling numerical data (e.g., landmark coordinates)
seaborn (optional): For enhanced plot styling


A dataset or variables defining:
M: A 2D NumPy array of landmark coordinates ([x, y])
est_traj: A list of estimated trajectory points ([[x1, y1], [x2, y2], ...])
data['gt']: A list of ground truth points ([[x1, y1], [x2, y2], ...])



Installation

Clone the Repository (if applicable):
git clone <repository-url>
cd <repository-directory>


Set Up a Virtual Environment (recommended):
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install Dependencies:
pip install matplotlib numpy seaborn

Note: If you don't want to use Seaborn, you can skip it and use a built-in Matplotlib style (e.g., ggplot).

Verify Matplotlib Version: Ensure you're using Matplotlib 3.6 or higher for compatibility with Seaborn styles:
python -c "import matplotlib; print(matplotlib.__version__)"



Usage

Prepare Your Data: Ensure the following variables are defined in your Python script or environment:

M: A NumPy array of shape (n, 2) for n landmarks, where each row is [x, y].
est_traj: A list of estimated trajectory points, where each point is [x, y].
data: A dictionary with a 'gt' key containing a list of ground truth points [x, y].

Example dummy data:
import numpy as np
M = np.array([[1, 1], [2, 2], [3, 3]])
est_traj = [[1.1, 1.1], [2.1, 2.1], [3.1, 3.1]]
data = {'gt': [[1, 1], [2, 2], [3, 3]]}


Run the Visualization Script: Use the provided Python script to generate the plot. Save the following code as plot_ekf.py and run it:
import matplotlib.pyplot as plt
import numpy as np

# Check if seaborn is installed and use appropriate style
try:
    import seaborn
    plt.style.use('seaborn-v0_8')
except ImportError:
    print("Seaborn not installed. Falling back to 'ggplot' style.")
    plt.style.use('ggplot')

plt.figure(figsize=(10, 8))

try:
    plt.plot(M[:, 0], M[:, 1], '^r', markersize=10, label='Landmarks')
except NameError:
    print("Error: 'M' is not defined. Please provide a valid 2D NumPy array.")
    raise

try:
    plt.plot([p[0] for p in est_traj], [p[1] for p in est_traj], '.g', markersize=15, label='Estimated Trajectory')
except NameError:
    print("Error: 'est_traj' is not defined. Please provide a valid list of points.")
    raise

try:
    plt.plot([p[0] for p in data['gt']], [p[1] for p in data['gt']], '--b', linewidth=2, label='Ground Truth')
except (NameError, KeyError):
    print("Error: 'data' or 'data['gt']' is not defined. Please provide a valid dictionary with 'gt' key.")
    raise

plt.legend(loc='upper right')
plt.title('EKF Localization', fontsize=16)
plt.xlabel('X (meters)', fontsize=12)
plt.ylabel('Y (meters)', fontsize=12)
plt.grid(True, which='both', linestyle='--', alpha=0.7)
plt.minorticks_on()
plt.axis('equal')
plt.show()

Run the script:
python plot_ekf.py


Expected Output: A plot will display showing:

Red triangles (^r) for landmarks.
Green dots (.g) for the estimated trajectory.
Blue dashed lines (--b) for the ground truth. The plot includes a grid, legend, and labeled axes for clarity.



Troubleshooting

Seaborn Error: If you see OSError: 'seaborn' is not a valid package style, ensure Seaborn is installed (pip install seaborn) or use a built-in style like ggplot:
plt.style.use('ggplot')


Data Errors: If variables (M, est_traj, data['gt']) are undefined, define them as shown in the example data above.

Matplotlib Version: Check available styles with:
import matplotlib.pyplot as plt
print(plt.style.available)

Use a style from this list if seaborn-v0_8 fails.


Contributing
Contributions are welcome! To contribute:

Fork the repository.
Create a new branch (git checkout -b feature-branch).
Make changes and commit (git commit -m "Add feature").
Push to your fork (git push origin feature-branch).
Create a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details (if applicable).
Contact
For questions or issues, please open an issue on the repository or contact [your email or preferred contact method].

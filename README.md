
# FyveBy Technical Challenge

## Project Overview

This project addresses a technical challenge for tracking an airplane in 3D space using a sequence of fused point cloud frames (from 4 LiDAR sensors). The main goal is to identify and track a consistent point on the airplane as it moves through space, using only geometric and clustering techniques—no advanced state estimation is required.

## Problem Statement
- **Input:** A sequence of point cloud frames (`.ply` files) containing an airplane in different positions.
- **Output:** The (x, y, z) coordinates of a consistent tracking point on the airplane across all frames.

## Solution Approach
1. **Preprocessing:**
	- Remove outliers and downsample the point cloud for efficient processing.
2. **Clustering:**
	- Use DBSCAN clustering to segment the point cloud and identify airplane-like clusters based on geometric heuristics (bounding box dimensions, aspect ratio).
3. **Tracking Point Extraction:**
	- Use PCA to find the principal axes of the airplane cluster and select a consistent point (e.g., the tail) as the tracking point.
4. **Visualization:**
	- Plot the trajectory of the tracking point in 2D and 3D.

## Project Structure
```
Technical-Challenege/
│   FyveBy_TechicalChallenge.ipynb   # Main notebook with code and explanations
│   README.md                       
└───data/
	  frame_1.ply
	  frame_2.ply
	  ...
	  frame_10.ply
```

## Key Files
- **FyveBy_TechicalChallenge.ipynb**: Contains all code, explanations, and answers to follow-up questions.
- **data**: Contains point cloud frames in `.ply` format.

## Main Libraries Used
- **numpy**: Numerical operations and array handling.
- **open3d**: Point cloud processing, filtering, clustering, and visualization.
- **matplotlib**: 2D and 3D plotting of point clouds and trajectories.
- **scipy**: (Optional, not directly used in the provided code, but useful for scientific computing.)

## Environment Requirements
- Python 3.10 (recommended)
- numpy
- open3d
- matplotlib

## Installation
1. **Clone the repository**:
	```powershell
	git clone https://github.com/SwarajMundruppadyRao/Technical-Challenege.git
	cd Technical-Challenege
	```
2. **Create a virtual environment (optional but recommended):**
	```powershell
	python -m venv venv
	.\venv\Scripts\activate
	```
3. **Install dependencies:**
	```powershell
	pip install numpy open3d matplotlib
	```

## How to Run
1. Open `FyveBy_TechicalChallenge.ipynb` in Jupyter Notebook or VS Code.
2. Run all cells in order. The notebook will:
	- Load each `.ply` file from the `data/` folder
	- Preprocess, cluster, and extract the tracking point
	- Plot the trajectory of the tracked point
3. Review the code comments and markdown cells for explanations and follow-up answers.

## Assumptions
- The airplane is the largest above-ground object in each frame.
- The tail (or another consistent part) is always visible and can be tracked using PCA.
- The point cloud data is already fused and aligned.

## Extending the Solution
- **Real-time Performance:**
  - Restrict clustering to a region of interest around the last known location.
  - Use faster clustering methods if needed.
  - Downsample point clouds for speed.
- **Orientation Tracking:**
  - Use PCA to extract the principal axis for orientation.
- **Collision Detection:**
  - See notebook for pseudocode and algorithmic outline.

## Notes
- The approach is geometric and interpretable, making it adaptable to other similar problems.

## References
- [Open3D Documentation](http://www.open3d.org/docs/latest/)
- [Matplotlib Documentation](https://matplotlib.org/stable/)
- [NumPy Documentation](https://numpy.org/doc/)

---
For any questions, please refer to the explanations and Q&A sections in the notebook.

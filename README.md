# 3D Object Reconstruction from Multi-View Images

Reconstruct a 3D point cloud of a physical object from overlapping 2D photographs using computer vision, then show it using Open3D.

## Project Setup

From the project root in **PowerShell**:

1. Create the virtual environment:
`python -m venv .venv`

2. Activate it:
`.\.venv\Scripts\Activate.ps1`

> [!IMPORTANT]
> If blocked, first run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`

> [!NOTE]
> On macOS/Linux, activate with `source .venv/bin/activate` instead.

3. Install dependencies:
`pip install opencv-python open3d`

4. Verify the install:
`python -c "import cv2, numpy, open3d; print('OK')"`

## Camera Calibration

1. Print a checkerboard (default: 9x6 inner corners, i.e. 10x7 squares) and tape it flat to a rigid surface.
2. Take 15-20 photos of it from varied angles with the same phone lens used for the object, export them at the same resolution, and put them in `images/calibration_images/`.
3. Run calibration (results are saved to `results/calibration.npz`):
`python src/main.py --square-size <square side in mm>`

Use `--pattern COLS ROWS` for a different board, `--show-corners` to save detection overlays, and `--recalibrate` to redo it.

## Project Idea

* Capture ~20-40 images of one textured object
* Calibrate the camera
* Detect and match features
* Estimate camera pose and triangulate matches
* Display the resulting point cloud in Open3D
* Number of images
* Feature detector (SIFT, Harris, Shi-Tomasi, FAST)
* Camera spacing / viewpoint change

## Technologies

Python, OpenCV, NumPy, Open3D

## References


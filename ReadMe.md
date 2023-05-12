# Morphing Readme

This code performs image morphing by warping one image onto the structure of another image based on a set of corresponding points. The code is written in Python 3 and requires several external libraries such as OpenCV, DLib, Numpy, Scipy and Imageio.

## Libraries

This code requires the following libraries to be installed in your Python environment:

- dlib
- cv2 (OpenCV)
- numpy
- imageio
- scipy

You can install these libraries using pip. For example:

```
pip install dlib
pip install opencv-python
pip install numpy
pip install imageio
pip install scipy
```

## Preprocessing

Before performing the morphing, the code pre-processes the input images by performing the following steps:

- Reading the images
- Converting them to grayscale
- Detecting faces in the images using DLib
- Adding some boundary points to the detected landmark points
- Performing Delaunay triangulation on the landmark points to get a set of triangles that cover the face

The `PreMorph` function performs all these preprocessing steps and returns the input images along with the triangle points.

## Morphing

The morphing algorithm works as follows:

- For each point in the triangles, compute a corresponding point on the target triangle using affine transformation
- Use the computed points to create a warp matrix using OpenCV's `getAffineTransform` function
- Warp the source image into the target image using OpenCV's `warpAffine` function

The `morph_points` function computes the corresponding points on the target triangle, and the `warp_images` function warps the source image into the target image using the computed warp matrix.
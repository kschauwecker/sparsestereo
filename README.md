General Information
===================

This is the code for the [IROS 2012 paper "A New Feature Detector and Stereo Matching
Method for Accurate High-Performance Sparse Stereo Matching"](paper_iros2012.pdf).
**The code has not been updated since it's original publication.**
Please use at your own risk.

The provided source code package contains an efficient sparse stereo analysis algorithm
that applies a dense consistency check, leading to accurate matching results.
Matching accuracy is further improved by the new feature detector exFAST (extended FAST),
which is based on FAST but exhibits a less clustered feature distribution. This feature detector
leads to a superior performance of our stereo analysis algorithm. For details about both
methods please consult our publication [1].


Implementation Details
======================

The source code makes heavy use of the GCC vector extensions to take advantage
of the SSE instruction sets. Hence, the code cannot be complied with a
different compiler without making major modifications.

We included a simple example application that demonstrates how to use our code.
Also included is one example stereo pair with a matching camera calibration
file.

Some notes about camera calibration: We use the OpenCV functions
stereoCalibrate and stereoRectify to obtain the calibration and rectification
data. The example application loads those settings from an XML file. The
meaning of the individual data items is as follows:

- **M1:** Camera matrix of left camera (from stereoCalibrate)
- **M2:** Camera matrix of right camera (from steroCalibrate)
- **D1:** Distortion coefficients for left camera (from stereoCalibrate)
- **D2:** Distortion coefficients for right camera (from stereoCalibrate)
- **R1:** Rectification transformation for left camera (from stereoRectify)
- **R2:** Rectification transformation for right camera (from stereoRectify)
- **P1:** Projection matrix for left camera (from stereoRectify)
- **P2:** Projection matrix for right camera (from stereoRectify)
- **Q:**  Disparity-to-depth mapping matrix (from stereoRectify)
- **size:** Image size of one camera image

License
=======

This source code is published under the GNU General Public License version 3,
of which a copy is distributed with this code. Exempt from this license is the
FAST9 detector (file: src/sparsestereo/fast9-inl.h), which was originally
written by Edward Rosten and has only been modified by us.

Paper
=====

If you use our code for any research that will be published, we kindly ask you
to cite our paper:

[1] Konstantin Schauwecker, Reinhard Klette, and Andreas Zell. A New Feature
Detector and Stereo Matching Method for Accurate High-Performance Sparse Stereo
Matching. In IEEE/RSJ International Conference on Intelligent Robots and
Systems (IROS). IEEE, October 2012.

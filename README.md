# Extended Kalman Filter
The goal of this project is to implement an extended Kalman filter in C++. Simulated data  of lidar and radar measurements are given representing a detected bicycle that travels around the vehicle. By using the Kalman filter, lidar measurements and radar measurements  we track the bicycle's position and velocity.

---

## Content of this Repo

* `src` The source directory
	  * `main.cpp` Reads in data, calls a function to run the Kalman filter, calls a function to calculate RMSE
	  * `FusionEKF.cpp` Initializes the filter, calls the predict function, calls the update function
	  * `kalman_filter.cpp` Defines the predict function, the update function for lidar, and the update function for radar
      * `tools.cpp` Function to calculate RMSE and the Jacobian matrix
* `data` A directory with input file
* `results` A directory with the outut files
* `Docs` A directory with files formats description
* `ide_profiles` A directory containing info about configurations for different IDEs
* `build` A directory containing Eclipse project and aconfigurations
* `cmake_build` A directory containing the build files uisng cmake and make tools.
* `kalman-tracker.py` The script that connects the C++ executable with the simulator


## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir cmake_build && cd cmake_build`
3. Compile: `cmake .. && make` 
   * On windows, you may need to run: `cmake .. -G "Unix Makefiles" && make`
4. Run it: `./ExtendedKF path/to/input.txt path/to/output.txt`. You can find
   some sample inputs in 'data/'.
    - eg. `./ExtendedKF ../data/obj_pose-laser-radar-synthetic-input.txt output.txt`

## Editor Settings

The editor used is Eclipse v4.6.3. However the source code compiles and builds with make and cmake tools. You can find the eclipse project and all configurations in the build folder. The folder cmake_build includes the files created with cmake and make tools.




## Use the simulator
1. First open the simulator program (Preferred settings are windowed 1600 x 900 with Simple)
2. Click Record Data in the simulator, a browser will then open to where you want to save your text file output. Make sure the path is the same as where kalman_tracker.py file is.
3. Run kalman_tracker.py with path to your compiled c++ file.
4. Click Run in the simulator to see estimation markers and RMSE values displayed in real time as measurement markers are collected.

Download Links for Kalman Filter Tracker Visualization tool:

 - [Windows](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58d07003_kalman-tracker-windows/kalman-tracker-windows.zip)
 - [Mac](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58d07064_kalman-tracker-mac.app/kalman-tracker-mac.app.zip)
 - [Linux](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58d96544_kalman-tracker-linux/kalman-tracker-linux.zip)

The script `kalman-tracker.py` requires 1 argument which is the path to your compiled c++ file. Here is an example for how to call the script.

`python kalman_tracker.py .\build\ExtendedKF`

## Results

The Accuracy - RMSE is [0.0972256, 0.0853761, 0.450855, 0.439588] for the variables [px,py,vx,vy] representing the x position, y position, velocity on x position, velocity on y position respectively.

The accuracy is accepted since it is below the upper boundaries: [0.11, 0.11, 0.52, 0.52].

The green triangles represent our predictions regarding the bicycle position.

![](http://i.imgur.com/ovurM6B.jpg)
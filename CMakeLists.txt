cmake_minimum_required(VERSION 2.4)

PROJECT(MOTION_DETECTION)
# paths 
INCLUDE_DIRECTORIES(./)
INCLUDE_DIRECTORIES(/usr/local/include)
FIND_PACKAGE(OpenCV REQUIRED)
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})
LINK_DIRECTORIES(/usr/local/lib)
LINK_DIRECTORIES(/usr/lib)
SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR})
SET(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR})
SET(CMAKE_CXX_FLAGS "-o3 -w")
# SET(CMAKE_CXX_LINK_FLAGS "-pg") # dont want to profile each execution
SET(OpenCV_LIBRARIES opencv_core opencv_highgui opencv_imgproc opencv_video)

ADD_EXECUTABLE(motion-detection motion_detection.cpp)
ADD_EXECUTABLE(motion-seeker motion_seeker.cpp)
TARGET_LINK_LIBRARIES(motion-detection ${OpenCV_LIBRARIES})
TARGET_LINK_LIBRARIES(motion-seeker ${OpenCV_LIBRARIES})

SET(CMAKE_BUILD_TYPE Release)


PROJECT( eyeGaze )
FIND_PACKAGE( OpenCV REQUIRED )
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

cmake_minimum_required(VERSION 2.8)

include_directories( ${OPENGL_INCLUDE_DIRS}  ${GLUT_INCLUDE_DIRS} )
add_subdirectory(dlib/dlib dlib_build)
ADD_EXECUTABLE( eyeGaze oic.cpp util.cpp util.h pupilDetection.h pupilDetection.cpp faceDetection.cpp faceDetection.h kalmanFilters.h kalmanFilters.cpp constants.h  gazeComputation.cpp gazeComputation.h  gestureDetection.cpp gestureDetection.h kmeansUtils.cpp kmeansUtils.h pupilCdf.cpp pupilCdf.h viewUtils.h viewUtils.cpp)
target_link_libraries(eyeGaze dlib::dlib)
TARGET_LINK_LIBRARIES( eyeGaze ${OpenCV_LIBS} )


target_link_libraries(eyeGaze ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} )



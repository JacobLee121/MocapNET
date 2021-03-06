project( BVHGUI ) 
cmake_minimum_required( VERSION 2.8.7 )   
#cmake_minimum_required(VERSION 3.5)
find_package(OpenCV REQUIRED)
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})

#set_property(GLOBAL PROPERTY USE_FOLDERS ON)
set(CMAKE_CXX_STANDARD 11)  
include_directories(${TENSORFLOW_INCLUDE_ROOT})


add_executable(BVHGUI ${BVH_SOURCE} ${OPENGL_SOURCE} bvhgui.cpp ../MocapNET1/MocapNETLib/opengl.cpp ../MocapNET1/MocapNETLib/bvh.cpp ../MocapNET1/MocapNETLib/csv.cpp ../MocapNET1/MocapNETLib/visualization.cpp ../MocapNET1/MocapNETLib/remoteExecution.cpp ../MocapNET1/MocapNETLib/tools.cpp ../MocapNET1/MocapNETLib/jsonCocoSkeleton.cpp  ../MocapNET1/MocapNETLib/jsonMocapNETHelpers.cpp ../../dependencies/InputParser/InputParser_C.cpp ../MocapNET1/MocapNETLib/gestureRecognition.cpp ../MocapNET1/MocapNETLib/outputFiltering.cpp ../Tensorflow/tensorflow.cpp ../Tensorflow/tf_utils.cpp  )

target_link_libraries(BVHGUI rt dl m pthread ${OpenCV_LIBRARIES} ${OPENGL_LIBS} Tensorflow  TensorflowFramework MocapNETLib ${NETWORK_CLIENT_LIBRARIES} ${PNG_Libs} ${JPG_Libs} )
set_target_properties(BVHGUI PROPERTIES DEBUG_POSTFIX "D") 


set_target_properties(BVHGUI PROPERTIES 
                       ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"
                       LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"
                       RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}"
                      )


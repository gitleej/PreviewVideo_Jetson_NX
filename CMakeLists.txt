cmake_minimum_required(VERSION 3.10.2)
project(PreviewVideo_Jetson_NX)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# Set Spinnaker SDK
find_package(Spinnaker REQUIRED)
if (Spinnaker_FOUND)
    message("Spinnaker found.")
    message("spinnaker lib :   " ${Spinnaker_LIBRARIES})
    message("spinnaker include :   " ${Spinnaker_INCLUDE_DIRS})
endif ()

# OpenCV
find_package(OpenCV 4 REQUIRED)
if(OpenCV_FOUND)
    message("OpenCV found.")
    message("OpenCV lib :   " ${OpenCV_LIBRARIES})
    message("OpenCV include :   " ${OpenCV_INCLUDE_DIRS})
endif()

include_directories(
        ${Spinnaker_INCLUDE_DIRS}
        ${OpenCV_INCLUDE_DIRS}
)

add_executable(PreviewVideo_Jetson_NX Acquisition.cpp)

target_link_libraries(PreviewVideo_Jetson_NX
        ${Spinnaker_LIBRARIES}
        ${OpenCV_LIBRARIES}
        )

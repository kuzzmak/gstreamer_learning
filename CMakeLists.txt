cmake_minimum_required(VERSION 3.22)

# Set the project name and version
project(GStreamerLearning VERSION 1.0)

# Find the GStreamer package
find_package(PkgConfig REQUIRED)
pkg_check_modules(GST REQUIRED gstreamer-1.0)

# Add the executable
add_executable(gstreamer_learning src/basic-tutorial-1.c)

# Include the GStreamer headers
target_include_directories(gstreamer_learning PRIVATE ${GST_INCLUDE_DIRS})

# Link the GStreamer libraries
target_link_libraries(gstreamer_learning ${GST_LIBRARIES})

cmake_minimum_required(VERSION 3.22)

# Set the project name and version
project(GStreamerLearning VERSION 1.0)

# Find the GStreamer package
find_package(PkgConfig REQUIRED)
pkg_check_modules(GST REQUIRED gstreamer-1.0)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

# Get all source files in the src directory
file(GLOB SOURCES "src/*.c")

# Create an executable for each source file
foreach(SOURCE_FILE ${SOURCES})
    # Get the filename without the extension
    get_filename_component(EXECUTABLE_NAME ${SOURCE_FILE} NAME_WE)
    
    # Add the executable
    add_executable(${EXECUTABLE_NAME} ${SOURCE_FILE})
    
    # Include the GStreamer headers
    target_include_directories(${EXECUTABLE_NAME} PRIVATE ${GST_INCLUDE_DIRS} ${GTK3_INCLUDE_DIRS})
    
    # Link the GStreamer libraries
    target_link_libraries(${EXECUTABLE_NAME} ${GST_LIBRARIES} ${GTK3_LIBRARIES})
endforeach()

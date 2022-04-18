project(rast)

set(CMAKE_CXX_STANDARD 17)

add_library(rast SHARED cpuInterface.cpp)

target_include_directories(rast PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
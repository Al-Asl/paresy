cmake_minimum_required(VERSION 3.24)

set(CMAKE_CUDA_ARCHITECTURES 75)

project(Paresy LANGUAGES CXX CUDA)

add_executable(Paresy gpu126.cu)

add_definitions(-DMEASUREMENT_MODE)

target_link_libraries(Paresy
    cuda
    cudart
)

set(CMAKE_CUDA_FLAGS_RELEASE "${CMAKE_CUDA_FLAGS_RELEASE} --generate-line-info")
target_compile_options(Paresy PRIVATE $<$<COMPILE_LANGUAGE:CUDA>:--extended-lambda>)
target_include_directories(Paresy PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/modified_libraries)
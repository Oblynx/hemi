CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
PROJECT(GPUIntegration)

FIND_PACKAGE(CUDA REQUIRED)

LIST(APPEND CMAKE_CXX_FLAGS "-std=c++11 -O3")
LIST(APPEND CUDA_NVCC_FLAGS "-ccbin $ENV{CXX} --compiler-options -fno-strict-aliasing -lineinfo -Xptxas -dlcm=cg")
# LIST(APPEND CUDA_NVCC_FLAGS "-gencode arch=compute_20,code=sm_20")
# LIST(APPEND CUDA_NVCC_FLAGS "-gencode arch=compute_30,code=sm_30")
LIST(APPEND CUDA_NVCC_FLAGS "-gencode arch=compute_35,code=sm_35")

INCLUDE_DIRECTORIES(..)

####################   Simple   #####################
#CUDA_ADD_EXECUTABLE(simple_hello 						simple/hello.cpp)
#CUDA_ADD_EXECUTABLE(simple_hello_lambda 			simple/hello_lambda.cpp)
#CUDA_ADD_EXECUTABLE(simple_saxpy				 			simple/saxpy.cpp)
#CUDA_ADD_EXECUTABLE(simple_hello_global simple/hello_global.cu)

####################   NBody    #####################
#CUDA_ADD_EXECUTABLE(nbody
#	nbody_vec4/nbody_vec4.cpp
#	nbody_vec4/nbody_vec4.cu
#)

####################   BlackScholes    #####################
CUDA_ADD_EXECUTABLE(blackscholes_array blackscholes_hemiarray/blackscholes.cpp)

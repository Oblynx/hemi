CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
PROJECT(GPUIntegration)

FIND_PACKAGE(CUDA REQUIRED)
INCLUDE(FindCUDA)

LIST(APPEND CMAKE_CXX_FLAGS "-std=c++11 -O2 ")
LIST(APPEND CUDA_NVCC_FLAGS --compiler-options -fno-strict-aliasing -lineinfo -Xptxas -dlcm=cg)
# LIST(APPEND CUDA_NVCC_FLAGS -gencode arch=compute_20,code=sm_20)
# LIST(APPEND CUDA_NVCC_FLAGS -gencode arch=compute_30,code=sm_30)
LIST(APPEND CUDA_NVCC_FLAGS -gencode arch=compute_35,code=sm_35)

INCLUDE_DIRECTORIES(..)

####################   Simple   #####################
ADD_EXECUTABLE(simple_hello 						simple/hello.cpp)
ADD_EXECUTABLE(simple_hello_lambda 			simple/hello_lambda.cpp)
ADD_EXECUTABLE(simple_saxpy				 			simple/saxpy.cpp)
CUDA_ADD_EXECUTABLE(simple_hello_global simple/hello_global.cu)

####################   NBody    #####################
#ADD_EXECUTABLE(nbody 				 nbody_vec4/nbody_vec4.cpp)
#CUDA_ADD_EXECUTABLE(nbody_cu nbody_vec4/nbody_vec4.cu)

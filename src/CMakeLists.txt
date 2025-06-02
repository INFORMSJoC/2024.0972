cmake_minimum_required(VERSION 3.10)
project(BPPMCFsolver)

set(CMAKE_CXX_STANDARD 17)

set(GUROBI_INC_DIR "/opt/gurobi1102/linux64/include")
set(GUROBI_LIB_DIR "/opt/gurobi1102/linux64/lib")

include_directories(${GUROBI_INC_DIR})
link_directories(${GUROBI_LIB_DIR})

set(CommonLibs pthread dl libgurobi_g++8.5.a libgurobi_c++.a libgurobi110.so)

set(OPT_FLAGS "-O3 -march=native -fwhole-program -flto")
set(WARNING_FLAGS "-Wall -Wextra -Wpedantic -Wuninitialized -Wno-ignored-attributes")
set(SANITIZERS_FLAGS "-fno-omit-frame-pointer -fsanizite=address -fsanitize=undefined -fsanitize=leak")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${WARNING_FLAGS} -Wvla ")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} ${SANITIZERS_LAGS}")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} ${OPT_FLAGS} ")

set (CMAKE_LINKER_FLAGS "${CMAKE_STATIC_LINKER_FLAGS} -D_GLIBCXX_PARALLEL")

add_executable(BPPMCFsolver main.cpp main.h 
	helper_functions.cpp helper_functions.h
	AFCSP.cpp AFCSP.h BPPLB.cpp BPPLB.h BPPUB.cpp BPPUB.h TS.cpp TS.h
         LF.cpp LF.h HF.cpp HF.h MFMB.cpp MFMB.h
	IP2RE.cpp IP2RE.h RM2GIFFRE.cpp RM2GIFFRE.h )

target_link_libraries(BPPMCFsolver ${CommonLibs})
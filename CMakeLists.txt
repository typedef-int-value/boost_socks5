CMAKE_MINIMUM_REQUIRED (VERSION 3.1)
project (socks5)

# The version number.
set (utility_VERSION_MAJOR 1)
set (utility_VERSION_MINOR 0)

# Build type
if(NOT CMAKE_BUILD_TYPE) 
    set(CMAKE_BUILD_TYPE Release)
endif(NOT CMAKE_BUILD_TYPE)

# C++ standard version
if(CMAKE_COMPILER_IS_GNUCXX)
    add_compile_options (-std=c++17 -fpermissive)
endif()
if(MSVC)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /std:c++17")
endif()

# additional dependencies
#INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/boost_1_68_0)
#LINK_DIRECTORIES(${PROJECT_SOURCE_DIR}/boost_1_68_0/stage/lib)
INCLUDE_DIRECTORIES(/mnt/d/opensources/boost_1_80_0)

if(${CMAKE_CXX_COMPILER_ID} EQUAL MSVC)

elseif(${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU")
  if (${CMAKE_CXX_COMPILER} STREQUAL "/opt/gcc-linaro-7.2.1-2017.11-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-g++")
    # for cross compile
    LINK_DIRECTORIES(/mnt/d/opensources/boost_1_80_0/stage/lib/)
  else()
    # for x86

  endif()
endif()

# executable 	
ADD_EXECUTABLE(boost_sock5 boost_socks5.cpp)
TARGET_LINK_LIBRARIES (boost_sock5 pthread)
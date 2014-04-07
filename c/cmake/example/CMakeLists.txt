# Example CMAKE file for C project

CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
PROJECT(Example)

#Uncomment to make makefiles verbose
#set(CMAKE_VERBOSE_MAKEFILE ON)

SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c99 -Wall -Wextra")
SET(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -g -DDEBUG")
SET(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -DNDEBUG -O3")

#Source Code
ADD_SUBDIRECTORY(src)
INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/src)

# Exe
ADD_EXECUTABLE(example ${SOURCE_FILES})


# My favorite part about cmake is this
# If I include FindPkgConfig
# It is super easy to include libraries into your project.
# Below is an example of including the base SDL2 library into this project

#INCLUDE(FindPkgConfig)
#PKG_SEARCH_MODULE(SDL2 REQUIRED sdl2)
#INCLUDE_DIRECTORIES(${SLD2_INCLUDE_DIRS})
#TARGET_LINK_LIBRARIES(example ${SDL2_LIBRARIES})


cmake_minimum_required(VERSION 3.21)

message("")
message( STATUS "CMAKE_BINARY_DIR: " ${CMAKE_BINARY_DIR} )
message( STATUS "CMAKE_SOURCE_DIR: " ${CMAKE_SOURCE_DIR} )
message( STATUS "CMAKE_COMMAND: " ${CMAKE_COMMAND} )
message( STATUS "CMAKE_VERSION: " ${CMAKE_VERSION} )
message( STATUS "CMAKE_C_COMPILER: " ${CMAKE_C_COMPILER} )
message( STATUS "CMAKE_PROJECT_NAME: " ${CMAKE_PROJECT_NAME} )
message( STATUS "CMAKE_FINDCMAKE: " ${CMAKE_SOURCE_DIR}/cmake )


if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
  message(STATUS "Linux System")
elseif(CMAKE_SYSTEM_NAME STREQUAL "Darwin")
  message(STATUS "Mac System")
elseif(CMAKE_SYSTEM_NAME STREQUAL "Windows")
  message(STATUS "Windows System")
else()
  message(STATUS "this is ${CMAKE_SYSTEM_NAME} host: ${CMAKE_HOST_SYSTEM_NAME}")
endif()


project(2d_engine)

## ------- Set Vars ------- #
set(CMAKE_CXX_STANDARD  20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/include/")

add_executable(2d_engine src/main.cpp)

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)
find_package(SDL2_mixer REQUIRED)

#message("")
#message( STATUS "FINDING SDL2" )
#message( STATUS "SDL2_FOUND: " ${SDL2_FOUND})
#message( STATUS "SDL2_INCLUDE_DIR:" ${SDL2_INCLUDE_DIRS})
#message( STATUS "SDL2_LIBRARY: " ${SDL2_LIBRARIES})
#message( STATUS "SDL2_IMAGE_LIBRARY: " ${SDL2_IMAGE_LIBRARIES})
#message( STATUS "SDL2_IMAGE_FOUND: " ${SDL2_IMAGE_FOUND})

include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_IMAGE_INCLUDE_DIR})
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL_IMAGE_LIBARIES})

  #
  #set(SOURCE_FILES    src/main.cpp)
  #
  #Message("")
  #Message( STATUS "SOURCE entry point : " ${SOURCE_FILES} )
  #Message("")
  #
  ## ------- End Set Vars --- #
  #
  #
  ## ------- Executable ----- #
  #
  #ADD_EXECUTABLE(2d_engine ${SOURCE_FILES})
  #
  ## ------- End Executable - #
  #

  #
  #
  #find_package(SDL2_IMAGE REQUIRED)
  #Message("")
  #Message( STATUS "FINDING  SDL2_IMAGE" )
  #if (${SDL2_IMAGE_FOUND})
  #    Message( STATUS "SDL2_IMAGE_FOUND: " ${SDL2IMAGE_FOUND})
  #    Message( STATUS "SDL2_INCLUDE_DIR:" ${SDL2_INCLUDE_DIRS})
  #    Message( STATUS "SDL2_LIBRARY: " ${SDL2_LIBRARIES})
  #else()
  #    Message( STATUS "SDL2_IMAGE_FOUND: " ${SDL2_IMAGE_FOUND})
  #    Message( FATAL_ERROR "SDL2_IMAGE NOT FOUND" )
  #endif()
  #
  ## file(COPY resources DESTINATION ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})
  #
  ## ------- Inc & Link ---- #
  #
  #INCLUDE_DIRECTORIES(${SDL2_INCLUDE_DIRS})
  #TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${SDL2_LIBRARIES})

  # ------- End ----------- #
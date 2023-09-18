cmake_minimum_required(VERSION 3.2)
project(cc-wrapper)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

include_directories(${CMAKE_CURRENT_LIST_DIR}/tinyjson)
file(GLOB SRCS "src/*.cpp")

add_subdirectory(tinyjson)

# Define the output
add_executable(cc-wrapper ${SRCS})
target_link_libraries(cc-wrapper ${LINKER_OPTIONS} tinyjson)

if(NOT WITHOUT_INSTALL)
    message(STATUS "Adding install target")
    install(TARGETS cc-wrapper DESTINATION ${CMAKE_INSTALL_PREFIX}/bin)
endif()


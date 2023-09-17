cmake_minimum_required(VERSION 3.2)
project(cc-wrapper)

include_directories(${CMAKE_SOURCE_DIR}/tinyjson)
file(GLOB SRCS "src/*.cpp")

add_subdirectory(tinyjson)

# Define the output
add_executable(cc-wrapper ${SRCS})
target_link_libraries(cc-wrapper ${LINKER_OPTIONS} tinyjson)

install(TARGETS cc-wrapper DESTINATION ${CMAKE_INSTALL_PREFIX}/bin)

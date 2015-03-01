project(makeItRobotics)
cmake_minimum_required(VERSION 3.1)

include_directories(
  ../../Arduino/hardware/arduino/cores/arduino
  ../../Arduino/hardware/arduino/variants/standard
  /usr/local/Cellar/avr-gcc/4.9.2/avr/include
  /usr/local/Cellar/avr-gcc/4.9.2/lib/gcc/avr/4.9.2/include-fixed
  $ENV{GTEST_HOME}/include)
  
link_directories(
  ../lib
  $ENV{GTEST_HOME}/mybuild)

add_definitions(-std=c++0x)

#set(CMAKE_CXX_COMPILER avr-gcc)
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -mmcu=atmega328p -DF_CPU=16000000UL -Os -w -Wl,--gc-sections -ffunction-sections -fdata-sections")

set(sources
  MakeItRobotics.cpp)

set(tests
  test/MakeItRobotics_test.cpp)

add_executable(test_runner ${sources})
target_link_libraries(test_runner arduino)
target_link_libraries(test_runner pthread)
#target_link_libraries(test_runner gtest_main)

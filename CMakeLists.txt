cmake_minimum_required(VERSION 2.6)
PROJECT(cmocka-hello)
ADD_DEFINITIONS(-Wall -Werror --std=gnu99 -Wmissing-declarations)

FILE(MAKE_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)

SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/build/modules")
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)

SET(SOURCES
	src/almost-calc.c
	src/almost-main.c
)

ADD_EXECUTABLE(almost-calc ${SOURCES})

FIND_PACKAGE(CMOCKA REQUIRED)
ADD_SUBDIRECTORY(tests)

INSTALL(TARGETS almost-calc RUNTIME DESTINATION bin)

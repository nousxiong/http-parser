#
# This file is part of the CMake build system for GCE
#
# Copyright (c) 2015 Nous Xiong (348944179 at qq dot com)
#
# Distributed under the Boost Software License, Version 1.0. (See accompanying
# file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)
#
# See https://github.com/nousxiong/http-parser for latest version.
#

cmake_minimum_required (VERSION 2.8.6 FATAL_ERROR)
project (http_parser)

if (CMAKE_COMPILER_IS_GNUCXX AND NOT MINGW)
  add_definitions (-fPIC)
endif ()

if (WIN32)
  # Set vc bigobj
  if (${CMAKE_GENERATOR} MATCHES "Visual Studio *")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /bigobj")
  endif ()
endif ()

# Set up all files.
file (GLOB HTTP_PARSER_HEADER_FILES "${PROJECT_SOURCE_DIR}/http_parser.h")
file (GLOB HTTP_PARSER_HEADER_FILES ${HTTP_PARSER_HEADER_FILES} "${PROJECT_SOURCE_DIR}/stdint.hpp")
file (GLOB HTTP_PARSER_SOURCE_FILES "${PROJECT_SOURCE_DIR}/http_parser.cpp")

# http_parser library
add_library (http_parser STATIC ${HTTP_PARSER_SOURCE_FILES} ${HTTP_PARSER_HEADER_FILES})

install (TARGETS http_parser ARCHIVE DESTINATION lib)
install (FILES ${HTTP_PARSER_HEADER_FILES} DESTINATION include)

# Copyright (C) 2006-2019 Istituto Italiano di Tecnologia (IIT)
# Copyright (C) 2006-2010 RobotCub Consortium
# All rights reserved.
#
# This software may be modified and distributed under the terms of the
# BSD-3-Clause license. See the accompanying LICENSE file for details.

cmake_minimum_required(VERSION 3.5)

find_package(YARP REQUIRED)

yarp_begin_plugin_library(userlib)
add_subdirectory(fake_grabber)
yarp_end_plugin_library(userlib)
add_executable(test_userlib test_userlib.cpp)

target_link_libraries(test_userlib ${YARP_LIBRARIES})
target_link_libraries(test_userlib userlib)

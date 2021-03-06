# Copyright (C) 2006-2019 Istituto Italiano di Tecnologia (IIT)
# All rights reserved.
#
# This software may be modified and distributed under the terms of the
# BSD-3-Clause license. See the accompanying LICENSE file for details.

# hmac
project(YARP_priv_hmac)

set(hmac_SRCS hmac/hmac_sha2.c
              hmac/sha2.c)

set(hmac_HDRS
    hmac/hmac_sha2.h
    hmac/sha2.h)

add_library(YARP_priv_hmac STATIC ${hmac_SRCS} ${hmac_HDRS})

set_property(TARGET YARP_priv_hmac PROPERTY FOLDER "Libraries/External")

set(hmac_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}/hmac PARENT_SCOPE)
set(hmac_LIBRARIES YARP_priv_hmac PARENT_SCOPE)
set(hmac_DEFINITIONS "" PARENT_SCOPE)

install(TARGETS YARP_priv_hmac
        EXPORT YARP_priv_hmac
        COMPONENT YARP_priv_hmac
        RUNTIME DESTINATION "${CMAKE_INSTALL_BINDIR}"
        LIBRARY DESTINATION "${CMAKE_INSTALL_LIBDIR}"
        ARCHIVE DESTINATION "${CMAKE_INSTALL_LIBDIR}")

if(NOT CREATE_SHARED_LIBS)
  include(YarpInstallBasicPackageFiles)
  yarp_install_basic_package_files(YARP_priv_hmac)
endif()

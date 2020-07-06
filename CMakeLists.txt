cmake_minimum_required(VERSION 3.9.10)
set(CMAKE_INSTALL_PREFIX /tmp)
project(hello_world)
add_executable(app main.cpp)
# --- install
set(CMAKE_INSTALL_PREFIX /tmp)
install(TARGETS app DESTINATION example/install/bin COMPONENT application)
# --- Package generation
set ( PACKAGE_NAME ${PROJECT_NAME} )
set ( PACKAGE_VERSION "1.1.0" )
set ( PACKAGE_RELEASE 0 )
set ( PACKAGE_DESCRIPTION_SUMMARY "Hello world program")
set(CPACK_GENERATOR "DEB;TGZ")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Nihal")
set(CPACK_COMPONENTS_ALL application )
#set(CPACK_MONOLITHIC_INSTALL 1)
#SET(CPACK_PACKAGING_INSTALL_PREFIX /tmp/)
#SET(CPACK_PACKAGING_INSTALL_DIRECTORY "/tmp")
#set(CPACK_MONOLITHIC_INSTALL 1)
set(CPACK_SET_DESTDIR ON)
# Debian packages
include(CPack)
if ( DPKG_FOUND )
    add_debian_package ( ${PROJECT_NAME} )
endif ( DPKG_FOUND )



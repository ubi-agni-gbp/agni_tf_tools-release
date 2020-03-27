cmake_minimum_required(VERSION 3.10.2)
project(agni_tf_tools)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED roscpp tf2_ros rviz)
message(STATUS "Using Qt ${rviz_QT_VERSION}")
find_package(Qt5 ${rviz_QT_VERSION} REQUIRED Core Widgets)
set(QT_LIBRARIES Qt5::Widgets)
find_package(Eigen3 REQUIRED)

## System dependencies are found with CMake's conventions
find_package(Boost REQUIRED COMPONENTS program_options)

include_directories(${EIGEN3_INCLUDE_DIRS} ${BOOST_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS})

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#  INCLUDE_DIRS include
  LIBRARIES agni_tf_tools
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)

###########
## Build ##
###########

## QT stuff
# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)
# Instruct CMake to run moc automatically when needed.
set(CMAKE_AUTOMOC ON)

#############
## sub dir ##
#############
add_subdirectory(src)

#############
## Install ##
#############

install(FILES
  plugin_description.xml
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

#############
## Testing ##
#############

## Add gtest based cpp test target and link libraries
# catkin_add_gtest(${PROJECT_NAME}-test test/test_agni_tf_tools.cpp)
# if(TARGET ${PROJECT_NAME}-test)
#   target_link_libraries(${PROJECT_NAME}-test ${PROJECT_NAME})
# endif()

## Add folders to be run by python nosetests
# catkin_add_nosetests(test)

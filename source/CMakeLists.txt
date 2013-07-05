cmake_minimum_required( VERSION 2.8.9 )

project( WeCut C CXX )

set( CMAKE_MODULE_PATH
     ${CMAKE_MODULE_PATH}
     ${CMAKE_CURRENT_SOURCE_DIR}/modules/MovingPixelBuild/source )

include( mpbCommon )

# Adding the Google test framework
set( GOOGLE_TEST_DIR modules/google-test )
include( mpbGoogleTest )

# Adding Qt5
include( libraries/mpbQt5 )

add_executable( WeCut src/main.cpp )
target_link_libraries( WeCut gtest gtest_main )

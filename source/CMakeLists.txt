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
find_package( Qt5Gui REQUIRED )

# Adding Kore
add_subdirectory( modules/libKore/source )
if( NOT KORE_FOUND )
    mpb_error_fatal( "Missing Kore library" )
endif( NOT KORE_FOUND )
message( "Inc: ${KORE_INCLUDES}" )
include_directories( ${KORE_INCLUDES} )

add_executable( WeCut src/main.cpp )
target_link_libraries( WeCut ${KORE_TARGET} )
qt5_use_modules( WeCut Gui )

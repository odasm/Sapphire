cmake_minimum_required(VERSION 3.0.2)
project(Sapphire)

include_directories( "../" )

file( GLOB UTILS_PUBLIC_INCLUDE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/*" )
file( GLOB UTILS_SOURCE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/src/*" )

set( CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} )

add_library( xivdat ${UTILS_PUBLIC_INCLUDE_FILES} ${UTILS_SOURCE_FILES} )

set_target_properties( xivdat PROPERTIES
        CXX_STANDARD 17
        CXX_STANDARD_REQUIRED ON
        CXX_EXTENSIONS ON
        )

if (UNIX)
    target_link_libraries( xivdat PUBLIC dl )
    target_link_libraries( xivdat PUBLIC z )
else()
    target_link_libraries( xivdat PUBLIC zlib )
endif()
target_include_directories( xivdat PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} )
#cotire( xivdat )

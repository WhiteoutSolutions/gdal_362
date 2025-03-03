# CMake4GDAL project is distributed under MIT license. See accompanying file LICENSE.txt.

set(GDAL_SWIG_COMMON_INTERFACE_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Band.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/ColorTable.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/cpl.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/cpl_exceptions.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/cplvirtualmem.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Dataset.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Driver.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/gdal.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/gdal_array.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/gdal_typemaps.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/gnm.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/MajorObject.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/ogr.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/ogr_error_map.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Operations.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/osr.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/RasterAttributeTable.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Relationship.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Transform.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/XMLNode.i
    ${CMAKE_CURRENT_SOURCE_DIR}/include/MultiDimensional.i)

# BUILD_PYTHON_BINDINGS is already defined in ../CMakeLists.txt
option(BUILD_JAVA_BINDINGS "Build Java bindings" ON)
option(BUILD_CSHARP_BINDINGS "Build CSharp bindings" OFF)

if (BUILD_PYTHON_BINDINGS)
  add_subdirectory(python)
endif ()
#
#if (SWIG_EXECUTABLE
#    AND Java_JAVAC_EXECUTABLE
#    AND Java_JAVADOC_EXECUTABLE
#    AND JNI_FOUND
#    AND ANT
#    AND BUILD_JAVA_BINDINGS)
#  add_subdirectory(java)
#endif ()



message(""***********HERE**********)
message(STATUS "SWIG_EXECUTABLE: ${SWIG_EXECUTABLE}")
message(STATUS "Java_JAVAC_EXECUTABLE: ${Java_JAVAC_EXECUTABLE}")
message(STATUS "Java_JAVADOC_EXECUTABLE: ${Java_JAVADOC_EXECUTABLE}")
message(STATUS "JNI_FOUND: ${JNI_FOUND}")
message(STATUS "ANT: ${ANT}")
message(STATUS "BUILD_JAVA_BINDINGS: ${BUILD_JAVA_BINDINGS}")


if (SWIG_EXECUTABLE
        AND Java_JAVAC_EXECUTABLE
        AND Java_JAVADOC_EXECUTABLE
        AND JNI_FOUND
        AND ANT
        AND BUILD_JAVA_BINDINGS)
  message(""***********MADE IT HERE**********)
  add_subdirectory(java)

endif ()


if (BUILD_CSHARP_BINDINGS
    AND SWIG_EXECUTABLE
    AND CSHARP_FOUND)
  add_subdirectory(csharp)
endif ()

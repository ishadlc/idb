add_library(libidb libidb.cpp)
add_library(idb::libidb ALIAS libidb)

set_target_properties(
    libidb
    PROPERTIES OUTPUT_NAME idb
)

target_compile_features(libidb PUBLIC cxx_std_17)

target_include_directories(libidb 
    PUBLIC
        $<INSTALL_INTERFACE:include>
        $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>        

    PRIVATE
        ${CMAKE_SOURCE_DIR}/src/include
)

include(GNUInstallDirs)
install(TARGETS libidb
    EXPORT idb-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(
    DIRECTORY ${PROJECT_SOURCE_DIR}/include/
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(
    EXPORT idb-targets
    FILE idb-config.cmake
    NAMESPACE idb::
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/idb
)
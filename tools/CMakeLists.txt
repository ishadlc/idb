add_executable(idb idb.cpp)
target_link_libraries(idb PRIVATE idb::libidb PkgConfig::libedit)
include(GNUInstallDirs)
install(
    TARGETS idb
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
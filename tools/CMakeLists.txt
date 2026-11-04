add_executable(idb idb.cpp)
target_link_libraries(idb PRIVATE idb::libidb)
include(GNUInstallDirs)
install(
    TARGETS idb
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
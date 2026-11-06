add_executable(tests tests.cpp)
target_link_libraries(tests PRIVATE idb::libidb Catch2::Catch2WithMain)
add_library(libidb libidb.cpp)
add_library(idb::libidb ALIAS libidb)

set_target_properties(
    libidb
    PROPERTIES OUTPUT_NAME idb
)

target_compile_features(libidb PUBLIC cxx_std_17)

target_include_directories(
    libidb
    PRIVATE include
    PUBLIC ${CMAKE_SOURCE_DIR}/include
)
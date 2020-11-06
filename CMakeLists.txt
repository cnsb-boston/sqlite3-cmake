PROJECT(sqlite3)
cmake_minimum_required(VERSION 2.8)

SET(CMAKE_C_FLAGS "-O3")

include_directories(${CMAKE_SOURCE_DIR}/src)
add_library(sqlite3 STATIC src/sqlite3.c src/sqlite3.h src/sqlite3ext.h)

add_definitions(-DSQLITE_ENABLE_RTREE)
add_definitions(-DSQLITE_ENABLE_FTS4)
add_definitions(-DSQLITE_ENABLE_FTS5)
add_definitions(-DSQLITE_ENABLE_DESERIALIZE)
add_definitions(-DSQLITE_OMIT_SHARED_CACHE)
add_definitions(-DSQLITE_OMIT_PROGRESS_CALLBACK)
add_definitions(-DSQLITE_OMIT_DEPRECATED)
add_definitions(-DSQLITE_OMIT_DECLTYPE)
add_definitions(-DHAVE_FDATASYNC)

# Uncomment this for single-threaded variant (faster)
add_definitions(-DSQLITE_THREADSAFE=0)

install(FILES src/sqlite3.h src/sqlite3ext.h DESTINATION include)

cmake_minimum_required(VERSION 3.1O)

# set the project name
project(Main.exe)

# enable modern C++

set(CMAKE_CXX_STANDARD 17)

# add the mylib library
add_subdirectory(mylib)

# add the executable
add_executable(Main.exe main.cpp)

target_link_libraries(Main.exe PUBLIC mylib)

# add the binary tree to the search path for include files
# so thath we will find mylib.h

target_include_directories(Main.exe PUBLIC "$(PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}/mylib")
install(TARGETS Main.exe DESTINATION bin)
install(FILES "${PROJECT_BINARY_DIR}/MyLib.h" DESTINATION include)

# Testing Support 
enable_testing()
find_package(GTest REQUIRED)

add_executable(Test.exe test.cpp)
target_link_libraries(Test.exe Gtest::GTest GTest::Main mylib)

# does the application run 
add_test(NAME Runs COMMAND  Main.exe)
add_test(AllTests Test.exe)


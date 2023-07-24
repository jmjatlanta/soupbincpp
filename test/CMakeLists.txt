cmake_minimum_required(VERSION 3.25 )
cmake_policy(VERSION 3.25)
set(CMAKE_CXX_STANDARD 17)

project ( soupbin_tests )

include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
FetchContent_MakeAvailable(googletest)

add_executable( soupbin_tests
    soupbin_server_tests.cpp
    soupbin_tests.cpp
    ../src/soup_bin_timer.cpp
    ../src/soup_bin_connection.cpp
)

target_include_directories(soupbin_tests PRIVATE 
    ../src
)

target_link_libraries(soupbin_tests 
    GTest::gtest
    GTest::gtest_main
)
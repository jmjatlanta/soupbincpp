cmake_minimum_required(VERSION 3.25 )
cmake_policy(VERSION 3.25)
set(CMAKE_CXX_STANDARD 17)

project ( soupbin_tests )

include(FetchContent)
FetchContent_Declare(
    googletest
    GIT_REPOSITORY https://github.com/google/googletest.git
    GIT_TAG v1.15.2
    DOWNLOAD_EXTRACT_TIMESTAMP ON
)
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

find_package(Boost 1.83 REQUIRED asio)

add_executable( soupbin_tests
    soupbin_server_tests.cpp
    soupbin_tests.cpp
    ../src/soup_bin_timer.cpp
    ../src/soup_bin_connection.cpp
)

target_include_directories(soupbin_tests PRIVATE 
    ../src
    ${BOOST_LIBRARY_INCLUDES}
)

target_link_libraries(soupbin_tests 
    Boost::asio
    GTest::gtest
    GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(soupbin_tests)

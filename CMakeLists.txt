cmake_minimum_required(VERSION 3.23)
project(knit LANGUAGES CXX)

########### set up for google tests ##############
#link : https://google.github.io/googletest/quickstart-cmake.html
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)
FetchContent_Declare(
    googleTest
    URL https://github.com/google/googletest/archive/7140cd416cecd7462a8aae488024abeee55598e4.zip
    DOWNLOAD_EXTRACT_TIMESTAMP true
)

#for windows: prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(
    hello_test
    tests/trial_test.cpp
)
target_link_libraries(
    hello_test
    GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_test)
#################### end set up for google test #########################
add_executable(knit)

target_sources(knit
    PRIVATE
        src/main.cpp
)

target_include_directories(knit PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)
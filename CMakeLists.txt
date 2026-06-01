cmake_minimum_required(VERSION 3.23)
project(knit LANGUAGES CXX)

add_executable(knit)

target_sources(knit
    PRIVATE
        main.cpp
)
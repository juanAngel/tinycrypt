cmake_minimum_required(VERSION 3.0)
project(tinycrypt) 

option(ENABLE_TESTING "activa la generacion de test" OFF)

include(lib/CMakeLists.txt)

if(ENABLE_TESTING)
    include(tests/CMakeLists.txt)
endif()

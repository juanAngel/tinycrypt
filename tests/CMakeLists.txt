
file(GLOB_RECURSE headers
    "${CMAKE_CURRENT_LIST_DIR}/include/*.h"
)
file(GLOB_RECURSE test_sources
    "${CMAKE_CURRENT_LIST_DIR}/*.c"
)
file(GLOB_RECURSE test_sources_exclude
    "${CMAKE_CURRENT_LIST_DIR}/test_ecc_utils.c"
)
list(REMOVE_ITEM test_sources ${test_sources_exclude})

foreach(test ${test_sources})
    get_filename_component(testName ${test} NAME_WE)
    message(STATUS "TEST ${testName} FOUND")

    add_executable(${testName} ${CMAKE_CURRENT_LIST_DIR}/${testName}.c ${test_sources_exclude} ${headers})
    target_include_directories(${testName} PUBLIC ${CMAKE_CURRENT_LIST_DIR}/include)
    target_link_libraries(${testName} ${PROJECT_NAME})
endforeach()

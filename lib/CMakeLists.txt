 
file(GLOB_RECURSE src
    "${CMAKE_CURRENT_LIST_DIR}/include/*.h"
    "${CMAKE_CURRENT_LIST_DIR}/source/*.c"
)
 
 add_library(${PROJECT_NAME} ${src})
 
 target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_LIST_DIR}/include)
 
if(MICROCHIP_MCU)
    target_link_libraries(${PROJECT_NAME}  Rexlab_os_crypto)
endif()
    

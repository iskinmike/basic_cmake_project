cmake_minimum_required ( VERSION 2.8.12 )

project ( base_project CXX )

set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --std=c++11 -g -O0")

# uncomment for submodule adding
# include_directories(submodule/include)
# include_directories(submodule/src)
# link_directories(submodule/build/lib)
# add_subdirectory(submodule)


set(SOURCES
    src/main.cpp
    include/base_project.hpp
)

set(LIBS
    ""
)

add_executable(${PROJECT_NAME} ${SOURCES})
# add_library(${PROJECT_NAME} SHARED ${SOURCES})

message(STATUS "base project CMAKE_CURRENT_BINARY_DIR:  ${CMAKE_CURRENT_BINARY_DIR}")
message(STATUS "base project CMAKE_CURRENT_LIST_DIR:  ${CMAKE_CURRENT_BINARY_DIR}")


target_include_directories ( ${PROJECT_NAME} BEFORE PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/include
        ${CMAKE_CURRENT_LIST_DIR}/src
)

target_link_libraries ( ${PROJECT_NAME} ${LIBS})

# target_compile_definitions(${PROJECT_NAME} PUBLIC -DARX_TARGET_PLATFORM_LINUX=1
#                                            PUBLIC -DDEBUG=1)

# uncomment to add custom targets and commands
# add_custom_target ( dist ALL
#     COMMAND ${CMAKE_COMMAND} -E remove_directory dist
#     COMMAND ${CMAKE_COMMAND} -E make_directory dist
#     COMMAND ${CMAKE_COMMAND} -E make_directory dist/result
#     COMMAND ${CMAKE_COMMAND} -E make_directory dist/resources
#     COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_CURRENT_LIST_DIR}/src/resources/* dist/resources/
# )
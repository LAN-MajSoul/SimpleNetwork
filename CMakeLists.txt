cmake_minimum_required(VERSION 3.11)
project(SimpleNetwork VERSION 0.1.0 LANGUAGES C CXX)

add_subdirectory(./extern/spdlog)
if(NOT TARGET spdlog)
    # Stand-alone build
    find_package(spdlog REQUIRED)
endif()

include(CTest)
enable_testing()

include_directories(./include/SimpleNetwork)

# aux_source_directory(. sources)
# aux_source_directory(./source/ sources)

file(GLOB sources CONFIGURE_DEPENDS ./source/*.cpp)

add_library(SimpleNetwork)
target_sources(SimpleNetwork PUBLIC ${sources})
target_link_libraries(SimpleNetwork PRIVATE spdlog::spdlog $<$<BOOL:${MINGW}>:ws2_32>)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

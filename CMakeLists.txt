cmake_minimum_required(VERSION 3.0.0)
project(SimpleNetwork VERSION 0.1.0 LANGUAGES C CXX)

include(CTest)
enable_testing()

include_directories(./include)

# aux_source_directory(. sources)
# aux_source_directory(./source/ sources)

file(GLOB sources CONFIGURE_DEPENDS ./source/*.cpp)

add_library(SimpleNetwork)
target_sources(SimpleNetwork PUBLIC ${sources})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

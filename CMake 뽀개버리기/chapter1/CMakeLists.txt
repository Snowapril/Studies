cmake_minimum_required(VERSION 3.18...3.20.3) # 가는하면 3.11+ 버전을 채택하는것 추천
project(hell-world VERSION 2021.7.10 LANGUAGES C CXX)

enable_language(ASM)

message(STATUS "hell world")

find_package(Threads REQUIRED)

set(HELL_WORLD "????")

# find fmtd.lib or fmt.lib
find_library(FMT_LIBPATH
    NAMES fmtd fmt
)

message(STATUS "Env path : $ENV{PATH}")
find_file(TXT_PATH 
    NAMES a.txt
    PATHS ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_SOURCE_DIR}
)
message(STATUS "Found txt : ${TXT_PATH}")
message(STATUS " - ${PROJECT_NAME}")
message(STATUS " - ${PROJECT_SOURCE_DIR}")
message(STATUS " - ${PROJECT_BINARY_DIR}")
message(STATUS " - ${PROJECT_VERSION_MAJOR}")
message(STATUS " - ${PROJECT_VERSION_MINOR}")
message(STATUS " - ${PROJECT_VERSION_PATCH}")


add_library(hell
    a.cpp
)

find_library(FMT_LIBPATH NAMES fmt fmtd)
if(FMT_LIBPATH)
    target_sources(hell
    PRIVATE
        use_fmt.cpp
        use_fmt2.cpp
    )
endif()
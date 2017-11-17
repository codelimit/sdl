cmake_minimum_required(VERSION 3.2)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall")

IF (MSVC)
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
    find_package(sdl2 REQUIRED)
    add_executable(main main.cpp)
    target_link_libraries(main PRIVATE SDL2::SDL2-static SDL2::SDL2main)

ELSEIF (MINGW)   

    set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++ -Wl,-Bstatic,--whole-archive -lwinpthread -Wl,--no-whole-archive")
    include_directories("C:/Program Files/mingw-w64/i686-7.2.0-posix-dwarf-rt_v5-rev0/mingw32/include")
    add_executable(main main.cpp)
    target_link_libraries(main mingw32 SDL2main SDL2 winmm imm32 version)

ELSEIF ()

    add_executable(main main.cpp)
    target_link_libraries(main SDL2main SDL2)

ENDIF()

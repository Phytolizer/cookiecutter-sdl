cmake_minimum_required(VERSION 3.12...3.22)

project(
    "{{cookiecutter.project_name}}"
    LANGUAGES "CXX"
    VERSION "{{cookiecutter.project_version}}"
    DESCRIPTION "{{cookiecutter.project_description}}"
    HOMEPAGE_URL "{{cookiecutter.project_homepage}}"
)

include(FetchContent)

FetchContent_Declare(
    "SDL"
    GIT_REPOSITORY "https://github.com/libsdl-org/SDL.git"
    GIT_TAG "release-2.0.16"
)
option(SDL_SHARED OFF)
set(LIBC ON)
FetchContent_MakeAvailable("SDL")

add_executable(
    "{{cookiecutter.project_name}}"
    "src/main.cpp"
)
target_link_libraries(
    "{{cookiecutter.project_name}}"
    PRIVATE "SDL2-static"
)
if(WIN32)
    target_link_libraries(
        "{{cookiecutter.project_name}}"
        PRIVATE "SDL2main"
    )
endif()

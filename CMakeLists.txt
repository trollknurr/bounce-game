cmake_minimum_required(VERSION 3.22)
include(FetchContent)

project(bounce
	VERSION 1.0.0
	LANGUAGES C
)

# set_property(GLOBAL PROPERTY USE_FOLDERS ON)

FetchContent_Declare(
	box2d
	GIT_REPOSITORY https://github.com/erincatto/box2d.git
	GIT_TAG main
	GIT_SHALLOW TRUE
	GIT_PROGRESS TRUE
)
FetchContent_MakeAvailable(box2d)

FetchContent_Declare(
	raylib
	GIT_REPOSITORY https://github.com/raysan5/raylib.git
	GIT_TAG master
	GIT_SHALLOW TRUE
	GIT_PROGRESS TRUE
)
FetchContent_MakeAvailable(raylib)


add_executable(game src/main.c)
target_link_libraries(game PRIVATE box2d raylib)

# if (APPLE)
#     target_link_libraries(${PROJECT_NAME} "-framework IOKit")
#     target_link_libraries(${PROJECT_NAME} "-framework Cocoa")
#     target_link_libraries(${PROJECT_NAME} "-framework OpenGL")
# endif()
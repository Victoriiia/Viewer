cmake_minimum_required(VERSION 3.10)
project(3D-viewer)

set(CMAKE_CXX_STANDARD 20)

# Пошук бібліотек
find_package(glm CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

# Додавання виконуваного файлу
add_executable(3D-viewer
    3D-viewer.cpp
    Vertex.h
    ViewerWindow.h
    ViewerWindow.cpp
    OpenglRenderSystem.h
    OpenglRenderSystem.cpp
    GeometryPrimitives.h
    GeometryPrimitives.cpp
    glad.c)

# Підключення бібліотек
target_link_libraries(3D-viewer PRIVATE glfw)

# Підключення папки із проектом, як джерела де шукати *.h\*.hpp файли
target_include_directories(3D-viewer PRIVATE ${CMAKE_SOURCE_DIR})

include_directories("C:/Users/user/3D-viewer/include")

# Додавання директиви GLFW_INCLUDE_NONE до проекту,
# що дозволить не використовувати вбудовані функції OpenGL бібліотеки GLFW, оскільки в нас є glad
target_compile_definitions(3D-viewer PRIVATE GLFW_INCLUDE_NONE)
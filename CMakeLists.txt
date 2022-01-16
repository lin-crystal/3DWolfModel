cmake_minimum_required(VERSION 3.20)
project(3Dproject)

set(CMAKE_CXX_STANDARD 14)

#设置一些OpenGL头文件所在目录的宏
set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include)
set(GLFW_H /usr/local/Cellar/glfw/3.3.4/include)
set(GLM_H /usr/local/Cellar/glm/0.9.9.8/include)
set(GLAD_H /usr/local/Cellar/glad/include)
set(ASSIMP_H /usr/local/Cellar/assimp/include)
#包含上述头文件所在目录
include_directories(${GLEW_H} ${GLFW_H} ${GLM_H} ${GLAD_H} ${ASSIMP_H})
include_directories(${PROJECT_SOURCE_DIR}/common)
include_directories(${PROJECT_SOURCE_DIR}/3DProject)

#设置OpenGL库所在位置，并链接
set(GLEW_LINK /usr/local/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.0.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3.4/lib/libglfw.3.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

add_executable(3DWolfModel
        3DWolfModel.cpp
        common/shader.cpp
        common/shader.hpp
        common/controls.cpp
        common/controls.hpp
        common/texture.cpp
        common/texture.hpp
        common/objloader.cpp
        common/objloader.hpp)





# mac下这步很重要
if (APPLE)
    target_link_libraries(3DWolfModel "-framework OpenGL")
    target_link_libraries(3DWolfModel "-framework GLUT")


endif()
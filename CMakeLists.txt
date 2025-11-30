cmake_minimum_required(VERSION 3.10)

# Project name
project(OpenGLApp LANGUAGES C CXX)

#C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add all file cpp/c
file(GLOB SRC_FILES
    ${PROJECT_SOURCE_DIR}/src/*.cpp
    ${PROJECT_SOURCE_DIR}/src/*.c
)

# Set debug mode
set(CMAKE_BUILD_TYPE Debug)


# # Output folder for all exe/lib
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# create add_executable
add_executable(OpenGLApp ${SRC_FILES})

# add include
target_include_directories(OpenGLApp PRIVATE
    ${PROJECT_SOURCE_DIR}/include
)

# Link lib (Windows vs Linux is different)
if (WIN32)
    # Windows: link to your lib
    target_link_directories(OpenGLApp PRIVATE ${PROJECT_SOURCE_DIR}/lib)

    target_link_libraries(OpenGLApp
        glfw3dll
        opengl32
    )
else()
    # Linux / Mac: Automatic find find_package
    find_package(OpenGL REQUIRED)
    find_package(glfw3 REQUIRED)

    target_link_libraries(OpenGLApp
        glfw
        ${OPENGL_gl_LIBRARY}
    )
endif()


# # ---- STATIC LINKING ON WINDOWS ----
# if (WIN32)
#     # where the lib files are
#     target_link_directories(OpenGLApp PRIVATE ${PROJECT_SOURCE_DIR}/lib)

#     # IMPORTANT: tell GLFW to use static build
#     target_compile_definitions(OpenGLApp PRIVATE GLFW_STATIC)

#     # Link libraries
#     target_link_libraries(OpenGLApp
#         glfw3            # <--- STATIC GLFW
#         opengl32
#     )
# endif()
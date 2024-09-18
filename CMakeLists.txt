cmake_minimum_required(VERSION 3.10)
project(ImGuiProject)

set(CMAKE_CXX_STANDARD 17)

# Set DirectX SDK path
set(DIRECTX_SDK_PATH "C:/Program Files (x86)/Microsoft DirectX SDK (June 2010)")

# Add ImGui source files
file(GLOB IMGUI_SOURCES 
    "${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/backend/*.cpp"
)

# Add your main.cpp
set(SOURCES ${IMGUI_SOURCES} main.cpp)

# Create executable
add_executable(${PROJECT_NAME} ${SOURCES})

# Include directories
target_include_directories(${PROJECT_NAME} PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui
    ${CMAKE_CURRENT_SOURCE_DIR}/backend
    "${DIRECTX_SDK_PATH}/Include"
)

# Link libraries
target_link_libraries(${PROJECT_NAME} PRIVATE 
    "${DIRECTX_SDK_PATH}/Lib/x64/d3d9.lib"
)

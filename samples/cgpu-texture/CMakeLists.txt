link_libraries(${SDL2_LIBRARIES})
include_directories(${SDL2_INCLUDES})

add_executable(TexturedBox
    texture.c
)
target_link_libraries(TexturedBox PUBLIC SakuraRuntime)

sakura_compile_shaders(TARGET TexturedBoxShaders
    SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/shaders/vertex_shader.vs_6_0.hlsl
            ${CMAKE_CURRENT_SOURCE_DIR}/shaders/fragment_shader.ps_6_0.hlsl
    DXIL    ${SAKURA_BIN_DIR}/resources/shaders/cgpu-texture
    SPIRV_DXC  ${SAKURA_BIN_DIR}/resources/shaders/cgpu-texture
)
add_dependencies(TexturedBox TexturedBoxShaders)
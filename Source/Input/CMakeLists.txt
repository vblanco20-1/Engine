project(input VERSION 1.0.0 DESCRIPTION "Input is a static library for Engine")

file(GLOB_RECURSE INPUT_FILES "*.cpp" "*.h")

add_library(${PROJECT_NAME} ${INPUT_FILES})
add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})
target_compile_definitions(${PROJECT_NAME} PUBLIC NOMINMAX _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(${PROJECT_NAME} PUBLIC
base::base
imgui::imgui
glfw ${GLFW_LIBRARIES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES FOLDER ${ROOT_FOLDER} LINKER_LANGUAGE CXX UNITY_BUILD ${UNITY_BUILD_ENABLED})
create_vs_filters(${INPUT_FILES})
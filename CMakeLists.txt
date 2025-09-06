cmake_minimum_required (VERSION 3.8)

if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("Platformer")

# SOURCES
set(source_cpp 
	"main.cpp"
)

# GAME
add_executable (Platformer  ${source_cpp})

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET Platformer PROPERTY CXX_STANDARD 20)
endif()

# SFML
set(SFML_DIR "C:/path/SFML/lib/cmake/SFML")

find_package(SFML 3.0 REQUIRED COMPONENTS Graphics Window System)

target_link_libraries(${PROJECT_NAME} PRIVATE 
    SFML::Graphics
    SFML::Window
    SFML::System
)
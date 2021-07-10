set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${ORBITER_BINARY_ROOT_DIR})

add_library(LuaInline SHARED
	LuaInline.cpp
)

target_include_directories(LuaInline
	PUBLIC ${ORBITER_SOURCE_SDK_INCLUDE_DIR}
)

target_link_libraries(LuaInline
	${ORBITER_LIB}
	${ORBITER_SDK_LIB}
	LuaInterpreter
	${LUA_LIB}
)

add_dependencies(LuaInline
	Orbiter
	Orbitersdk
	LuaInterpreter
)
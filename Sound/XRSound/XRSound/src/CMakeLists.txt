set(FORCE_DEBUG FALSE)

add_subdirectory(XRSoundLib)
add_subdirectory(XRSoundDLL)

ExternalProject_Add(XRSoundD
	PREFIX ${CMAKE_CURRENT_BINARY_DIR}/XRSoundLib/tmp
	BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR}/XRSoundLib/tmp
	SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/XRSoundLib
	INSTALL_DIR ${ORBITER_INSTALL_SDK_DIR}/XRSound
	CMAKE_GENERATOR Ninja
	CONFIGURE_COMMAND ${CMAKE_COMMAND} -A ${PLATFORM_STRING} -DCMAKE_BUILD_TYPE=Debug -DFORCE_DEBUG=TRUE -DORBITER_SOURCE_SDK_INCLUDE_DIR:PATH=${ORBITER_SOURCE_SDK_INCLUDE_DIR} -DORBITER_BINARY_SDK_DIR:PATH=${ORBITER_BINARY_SDK_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/XRSoundLib
)

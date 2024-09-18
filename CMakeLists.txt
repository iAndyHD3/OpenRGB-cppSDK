cmake_minimum_required(VERSION 3.0)

project(OpenRGB_cppSDK)


file(GLOB SOURCE_FILES
	"src/*.hpp" "src/*.cpp"
	"shared/CppUtils-Essential/*.hpp" "shared/CppUtils-Essential/*.cpp"
	"shared/CppUtils-Network/*.hpp" "shared/CppUtils-Network/*.cpp"
)

if(CMAKE_BUILD_TYPE MATCHES "Debug")
	add_compile_definitions(DEBUG SAFETY_CHECKS)
else()
	#add_compile_definitions(CRITICALS_CATCHABLE)
endif()

add_library(orgbsdk STATIC ${SOURCE_FILES})

target_include_directories(orgbsdk PUBLIC
	include
	shared/CppUtils-Essential
	shared/CppUtils-Network
)
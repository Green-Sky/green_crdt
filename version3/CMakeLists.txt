cmake_minimum_required(VERSION 3.9...3.24 FATAL_ERROR)

project(crdt_version3 CXX C)

add_library(crdt_version3 INTERFACE)

target_compile_features(crdt_version3 INTERFACE cxx_std_17)

target_include_directories(crdt_version3 INTERFACE "${PROJECT_SOURCE_DIR}")

########################################

if (BUILD_TESTING AND GREEN_CRDT_STANDALONE)

	add_executable(v3_test1
		./test1.cpp
	)
	target_link_libraries(v3_test1 PUBLIC crdt_version3)
	add_test(NAME v3_test1 COMMAND v3_test1)

########################################

	add_executable(v3_test2
		./test2.cpp
	)
	target_link_libraries(v3_test2 PUBLIC crdt_version3)
	add_test(NAME v3_test2 COMMAND v3_test2)

endif()


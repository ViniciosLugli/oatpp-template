cmake_minimum_required(VERSION 3.5)

set(project_name App)

project(${project_name})

set(CMAKE_CXX_STANDARD 11)

include_directories(src)

add_library(${project_name}-lib
	src/AppComponent.hpp
	src/controller/MyController.cpp
	src/controller/MyController.hpp
	src/dto/DTOs.hpp
)

# # link libs
find_package(oatpp 1.3.0 REQUIRED)

target_link_libraries(${project_name}-lib
	PUBLIC oatpp::oatpp
	PUBLIC oatpp::oatpp-test
)

# # add executables
add_executable(${project_name}-exe
	src/App.cpp
)
target_link_libraries(${project_name}-exe ${project_name}-lib)
add_dependencies(${project_name}-exe ${project_name}-lib)

add_executable(${project_name}-test
	test/tests.cpp
	test/app/TestComponent.hpp
	test/app/MyApiTestClient.hpp
	test/MyControllerTest.cpp
	test/MyControllerTest.hpp
)
target_link_libraries(${project_name}-test ${project_name}-lib)
add_dependencies(${project_name}-test ${project_name}-lib)

set_target_properties(${project_name}-lib ${project_name}-exe ${project_name}-test PROPERTIES
	CXX_STANDARD 11
	CXX_EXTENSIONS OFF
	CXX_STANDARD_REQUIRED ON
	LINKER_LANGUAGE CXX
)

enable_testing()
add_test(project-tests ${project_name}-test)

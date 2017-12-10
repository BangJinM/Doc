Cmake C++引用所有文件
```language
cmake_minimum_required(VERSION 3.8)
project(Arithmatic)

set(CMAKE_CXX_STANDARD 17)

file(GLOB SOURCE_FILES "*.cpp" "*.cc" "*.cxx")
file(GLOB HEADER_FILES "*.hpp" "*.hh" "*.hxx" "*.h")

add_executable(${PROJECT_NAME} ${SOURCE_FILES} ${HEADER_FILES})
```
cmake_minimum_required(VERSION 3.5)
project(conan_uvsslt)

include(${CMAKE_BINARY_DIR}/../conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

add_library(uv_ssl_t STATIC
    ./src/bio.c
    ./src/link_methods.c
    ./src/uv_ssl_t.c
)

target_include_directories(uv_ssl_t PUBLIC ./include)
target_include_directories(uv_ssl_t PRIVATE .)
target_link_libraries(uv_ssl_t PUBLIC CONAN_PKG::OpenSSL)
target_link_libraries(uv_ssl_t PUBLIC CONAN_PKG::libuv)
target_link_libraries(uv_ssl_t PUBLIC CONAN_PKG::uv_link_t)
target_link_libraries(uv_ssl_t PUBLIC CONAN_PKG::ringbuffer)

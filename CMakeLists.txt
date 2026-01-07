# TODO: Update cmake vers
cmake_minimum_required(VERSION 3.6)
set(CMAKE_TRY_COMPILE_TARGET_TYPE STATIC_LIBRARY)

project(c63_includeos)

find_package(IncludeOS REQUIRED)
include(os)

# Custom stuff
set(BINARY_NAME c63dec)
set(ELF_TARGET ${BINARY_NAME}${ELF_POSTFIX})

add_subdirectory(libc63)
include_directories(${CMAKE_SOURCE_DIR}/libc63)
link_directories(${CMAKE_BUILD_DIR}/libc63)
file(GLOB DEC_SRCS "decoder_srcs/*.cpp")

os_add_executable(c63dec "Codec 63 decoder in IncludeOS" ${DEC_SRCS})
os_add_drivers(c63dec virtiofs)
target_link_libraries(${ELF_TARGET} c63 m)
os_add_stdout(c63dec default_stdout)

set(ELF_SYMBOLS true)
install(TARGETS ${ELF_TARGET} DESTINATION bin)
include_directories("${source_dir}/include")
include_directories("${andersen_SOURCE_DIR}/include")

link_directories (${andersen_BINARY_DIR}/lib)

set (EXECUTABLE_OUTPUT_PATH ${andersen_BINARY_DIR}/unittest)
add_definitions(-DGTEST_HAS_RTTI=0)

# Add GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

add_executable(AndersTest AndersTest.cpp)
target_link_libraries(AndersTest LLVMAsmParser LLVMSupport LLVMCore AndersenStatic gtest_main ${GTEST_BOTH_LIBRARIES})

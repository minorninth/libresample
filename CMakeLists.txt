cmake_minimum_required(VERSION 3.0.0)

project(resample C)

include(CTest)

set(SRCS
    src/filterkit.c
    src/resample.c
    src/resamplesubs.c    
)

add_library(resample STATIC ${SRCS})

# Link libsndfile and libsamplerate for other tests
add_executable(resample_test tests/testresample.c)

target_link_libraries(resample_test PRIVATE resample)

add_test(NAME resample_test COMMAND resample_test)


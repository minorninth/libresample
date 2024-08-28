include(CheckIncludeFiles)

check_include_files(inttypes.h HAVE_INTTYPES_H)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/config.h.in ${CMAKE_CURRENT_SOURCE_DIR}/config.h)

add_library(libresample STATIC configtemplate.h
                               filterkit.c
                               filterkit.h
                               resample_defs.h
                               resample.c
                               resamplesubs.c
                               config.h)
target_include_directories(libresample PUBLIC ${libresample_INCLUDE_DIRECTORY})

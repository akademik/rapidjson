find_package(GTestSrc)

IF(GTESTSRC_FOUND)
    enable_testing()

    if (WIN32 AND (NOT CYGWIN) AND (NOT MINGW))
        set(gtest_disable_pthreads ON)
    endif()

    add_subdirectory(${GTEST_SOURCE_DIR} ${CMAKE_BINARY_DIR}/googletest)
    include_directories(${GTEST_INCLUDE_DIR})

    set(TEST_LIBRARIES gtest gtest_main)

    add_custom_target(tests ALL)
    add_subdirectory(perftest)
    add_subdirectory(unittest)

ENDIF(GTESTSRC_FOUND)

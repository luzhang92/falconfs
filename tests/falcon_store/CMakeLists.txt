include(GoogleTest)

enable_testing()
link_directories(${POSTGRES_SRC_DIR}/src/interfaces/libpq)

# ==================== FalconStoreUT =================
add_executable(FalconStoreUT
    ${PROJECT_SOURCE_DIR}/tests/falcon_store/test_falcon_store.cpp
    ${common_src}
)
target_link_libraries(FalconStoreUT
    FalconStore
    FalconClient
    zookeeper_mt
    glog
    jsoncpp
    gtest
    pq
    ${BRPC_LIBRARIES}
    ${DYNAMIC_LIB}
)

gtest_discover_tests(FalconStoreUT)

# ==================== FalconStoreThreadedUT =================
add_executable(FalconStoreThreadedUT
    ${PROJECT_SOURCE_DIR}/tests/falcon_store/test_falcon_store_threaded.cpp
    ${common_src}
)
target_link_libraries(FalconStoreThreadedUT
    FalconStore
    FalconClient
    zookeeper_mt
    glog
    jsoncpp
    gtest
    pq
    ${BRPC_LIBRARIES}
    ${DYNAMIC_LIB}
)

gtest_discover_tests(FalconStoreThreadedUT)

# ==================== FileLockUT =================
add_executable(FileLockUT
    ${PROJECT_SOURCE_DIR}/tests/falcon_store/test_file_lock.cpp
)
target_link_libraries(FileLockUT
    FalconStore
    gtest
)

gtest_discover_tests(FileLockUT)

# ==================== ReadStreamUT =================

add_executable(ReadStreamUT
    ${PROJECT_SOURCE_DIR}/tests/falcon_store/test_read_stream.cpp
    ${common_src}
)
target_link_libraries(ReadStreamUT
    FalconStore
    FalconClient
    zookeeper_mt
    glog
    jsoncpp
    gtest
    pq
    ${BRPC_LIBRARIES}
    ${DYNAMIC_LIB}
)

gtest_discover_tests(ReadStreamUT)

# ==================== NodeUT =================

add_executable(NodeUT
    ${PROJECT_SOURCE_DIR}/tests/falcon_store/test_node.cpp
    ${common_src}
)
target_link_libraries(NodeUT
    FalconStore
    FalconClient
    zookeeper_mt
    glog
    jsoncpp
    gtest
    pq
    ${BRPC_LIBRARIES}
    ${DYNAMIC_LIB}
)

gtest_discover_tests(NodeUT)

# ==================== DiskCacheUT =================

add_executable(DiskCacheUT
    ${PROJECT_SOURCE_DIR}/tests/falcon_store/test_disk_cache.cpp
)
target_link_libraries(DiskCacheUT
    FalconStore
    gtest
)

gtest_discover_tests(DiskCacheUT)

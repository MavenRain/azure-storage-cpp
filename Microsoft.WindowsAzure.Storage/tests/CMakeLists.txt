include_directories(../includes ${AZURESTORAGE_INCLUDE_DIRS} ${UnitTest++_INCLUDE_DIRS})

# THE ORDER OF FILES IS VERY /VERY/ IMPORTANT
if(UNIX)
  set(SOURCES
     blob_lease_test.cpp
     blob_streams_test.cpp
     blob_test_base.cpp
     cloud_blob_client_test.cpp
     cloud_blob_container_test.cpp
     cloud_blob_directory_test.cpp
     cloud_blob_test.cpp
     cloud_block_blob_test.cpp
     cloud_page_blob_test.cpp
     cloud_queue_client_test.cpp
     cloud_queue_test.cpp
     cloud_storage_account_test.cpp
     cloud_table_client_test.cpp
     cloud_table_test.cpp
     executor_test.cpp
     main.cpp
     queue_test_base.cpp
     read_from_secondary_test.cpp
     retry_policy_test.cpp
     service_properties_test.cpp
     stdafx.cpp
     storage_exception_test.cpp
     table_test_base.cpp
     test_base.cpp
    )
endif()

add_executable(${AZURESTORAGE_LIBRARY_TEST} ${SOURCES})

target_link_libraries(${AZURESTORAGE_LIBRARY_TEST} ${AZURESTORAGE_LIBRARIES} ${UnitTest++_LIBRARIES})

# Portions specific to cpprest binary versioning.
if(UNIX)
  set_target_properties(${AZURESTORAGE_LIBRARY_TEST} PROPERTIES
    SOVERSION ${AZURESTORAGE_VERSION_MAJOR}.${AZURESTORAGE_VERSION_MINOR})
endif()

# Copy test configuration to output directory
file(COPY test_configurations.json DESTINATION ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

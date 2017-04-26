add_library(
    rdkafka++
    ConfImpl.cpp
    ConsumerImpl.cpp
    HandleImpl.cpp
    KafkaConsumerImpl.cpp
    MessageImpl.cpp
    MetadataImpl.cpp
    ProducerImpl.cpp
    QueueImpl.cpp
    RdKafka.cpp
    TopicImpl.cpp
    TopicPartitionImpl.cpp
)

target_link_libraries(rdkafka++ PUBLIC rdkafka)

# Support '#include <rdkafcpp.h>'
target_include_directories(rdkafka++ PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}>")

set_target_properties(rdkafka++ PROPERTIES DEBUG_POSTFIX "${CMAKE_DEBUG_POSTFIX}")
install(
    TARGETS rdkafka++
    EXPORT "${targets_export_name}"
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    INCLUDES DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}"
)

install(
    FILES "rdkafkacpp.h"
    DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/librdkafka"
)

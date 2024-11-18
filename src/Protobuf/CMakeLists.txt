file(GLOB_RECURSE PROTOBUF_FILES "*.proto")

add_library(OpenSteamworksProtobufs ${PROTOBUF_FILES})

file(MAKE_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/Protobuf")

protobuf_generate(
    TARGET OpenSteamworksProtobufs
    LANGAUEG cpp
    PROTOC_OUT_DIR "${CMAKE_CURRENT_BINARY_DIR}/Protobuf"
)

target_include_directories(OpenSteamworksProtobufs
    PUBLIC
        "$<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}>;$<INSTALL_INTERFACE:OpenSteamworksProtobufs/>"
)

target_link_libraries(OpenSteamworksProtobufs
    PUBLIC
        protobuf::libprotobuf-lite
)

install(TARGETS OpenSteamworksProtobufs
    EXPORT OpenSteamworksProtobufs_Export
    ARCHIVE DESTINATION "lib"
    LIBRARY DESTINATION "lib"
    RUNTIME DESTINATION "bin"
    INCLUDES DESTINATION "include/OpenSteamworksProtobufs"
)

install(
    DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/Protobuf"
    DESTINATION "include/OpenSteamworksProtobufs"
)

install(
    EXPORT OpenSteamworksProtobufs_Export
    FILE "OpenSteamworksProtobufsTargets.cmake"
    NAMESPACE OpenSteamworks::
    DESTINATION "lib/cmake/OpenSteamworksProtobufs"
)

add_library(OpenSteamworksEMsg
    INTERFACE
        "$<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include/EMsg.hpp>;$<INSTALL_INTERFACE:OpenSteamworksProtobufs/include/EMsg.hpp>"
)
add_library(OpenSteamworks::EMsg ALIAS OpenSteamworksEMsg)

target_include_directories(OpenSteamworksEMsg
    INTERFACE
        $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include/>
        $<INSTALL_INTERFACE:OpenSteamworksProtobufs/>
)

install(TARGETS OpenSteamworksEMsg
    EXPORT OpenSteamworksProtobufsEMsg_Export
    ARCHIVE DESTINATION "lib"
    LIBRARY DESTINATION "lib"
    RUNTIME DESTINATION "bin"
    INCLUDES DESTINATION "include/OpenSteamworksProtobufs/EMsg"
    PUBLIC_HEADER DESTINATION "include/OpenSteamworksProtobufs/EMsg"
)

install(
    FILES
        "${CMAKE_SOURCE_DIR}/include/EMsg.hpp"
    DESTINATION "include/OpenSteamworksProtobufs/EMsg"
)

install(
    EXPORT OpenSteamworksProtobufsEMsg_Export
    FILE "OpenSteamworksProtobufsTargets.cmake"
    NAMESPACE OpenSteamworks::
    DESTINATION "lib/cmake/OpenSteamworksProtobufs"
)

add_subdirectory("Protobuf")

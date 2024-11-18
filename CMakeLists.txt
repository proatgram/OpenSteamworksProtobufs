cmake_minimum_required(VERSION 3.5)

project(OpenSteamworksProtobufs
    VERSION 0.1
    LANGUAGES CXX
    DESCRIPTION "Dumped Protobufs and an EMsg utility for the OpenSteamworks project."
    HOMEPAGE_URL "https://github.com/proatgram/OpenSteamworksProtobufs"
)

set(CMAKE_CXX_STANDARD 17)

include(FindProtobuf)
find_package(Protobuf REQUIRED)

add_subdirectory("src")

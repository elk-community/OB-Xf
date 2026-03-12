

add_subdirectory(sst/sst-cmake)
set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH}" PARENT_SCOPE)

# add_subdirectory(JUCE EXCLUDE_FROM_ALL)
get_target_property(_loc juce::juceaide IMPORTED_LOCATION)
message(STATUS "juceaide IMPORTED_LOCATION: ${_loc}")
message(STATUS "juceaide exists: ${_loc} -> $<TARGET_FILE_EXISTS:juce::juceaide>")

add_subdirectory(fmt EXCLUDE_FROM_ALL)

add_library(simde INTERFACE)
target_include_directories(simde INTERFACE simde)

add_subdirectory(sst/sst-cpputils EXCLUDE_FROM_ALL)
add_subdirectory(sst/sst-basic-blocks EXCLUDE_FROM_ALL)
add_subdirectory(sst/sst-plugininfra EXCLUDE_FROM_ALL)

add_subdirectory(melatonin_inspector EXCLUDE_FROM_ALL)
add_subdirectory(clap-juce-extensions EXCLUDE_FROM_ALL)

add_library(mts-client STATIC MTS-ESP/Client/libMTSClient.cpp)
target_include_directories(mts-client PUBLIC MTS-ESP/Client)

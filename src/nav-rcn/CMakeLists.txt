project(cai-nav-rcn)

file(GLOB NAV_H ./Nav/Include/*.h)
file(GLOB DETOUR_H ./Detour/Include/*.h)
file(GLOB DETOUR_CROWD_H ./DetourCrowd/Include/*.h)

aux_source_directory(./Detour/Source/ DETOUR_C)
aux_source_directory(./DetourCrowd/Source/ DETOUR_CROWD_C)
aux_source_directory(./Nav/Source/ NAV_C)

include_directories(./Detour/Include)
include_directories(./DetourCrowd/Include)
include_directories(./Nav/Include)

#ADD_DEFINITIONS(-DLUA_BUILD_AS_DLL)
#IF(MSVC)
##ADD_DEFINITIONS(-DNOUSE_JEMALLOC -DHAVE_STRUCT_TIMESPEC -DUSE_PTHREAD_LOCK)
#ENDIF()

add_library(cai-nav-rcn SHARED ${DETOUR__H} ${DETOUR_C} ${DETOUR_CROWD_H} ${DETOUR_CROWD_C} ${NAV_H} ${NAV_C})
IF(CMAKE_CL_64)
IF(MSVC)
set_target_properties(cai-nav-rcn PROPERTIES ARCHIVE_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
set_target_properties(cai-nav-rcn PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
ENDIF(MSVC)
ELSE(CMAKE_CL_64)
IF(MSVC)
set_target_properties(cai-nav-rcn PROPERTIES ARCHIVE_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
set_target_properties(cai-nav-rcn PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
ENDIF(MSVC)
ENDIF(CMAKE_CL_64)

#set(BUILD_USE_64BITS on)

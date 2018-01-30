project(nmgen-rcn)

file(GLOB NMGEN_RCN_H ./NMGen/Include/*.h)
file(GLOB RECAST_H ./Recast/Include/*.h)

aux_source_directory(./NMGen/Source/ NMGEN_RCN_C)
aux_source_directory(./Recast/Source/ RECAST_C)

include_directories(./NMGen/Include)
include_directories(./Recast/Include)

#ADD_DEFINITIONS(-DLUA_BUILD_AS_DLL)
#IF(MSVC)
##ADD_DEFINITIONS(-DNOUSE_JEMALLOC -DHAVE_STRUCT_TIMESPEC -DUSE_PTHREAD_LOCK)
#ENDIF()

add_library(nmgen-rcn SHARED ${NMGEN_RCN_H} ${NMGEN_RCN_C} ${RECAST_H} ${RECAST_C})
IF(CMAKE_CL_64)
IF(MSVC)
set_target_properties(nmgen-rcn PROPERTIES ARCHIVE_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
set_target_properties(nmgen-rcn PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
ENDIF(MSVC)
ELSE(CMAKE_CL_64)
IF(MSVC)
set_target_properties(nmgen-rcn PROPERTIES ARCHIVE_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
set_target_properties(nmgen-rcn PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ../../bin/x86_64)
ENDIF(MSVC)
ENDIF(CMAKE_CL_64)

#set(BUILD_USE_64BITS on)

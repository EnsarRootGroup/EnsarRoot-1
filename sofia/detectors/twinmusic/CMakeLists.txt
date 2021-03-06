# Create a library called "libSOFIATwinMusic" which includes the source files given in
# the array .
# Author: J.L. Rodriguez

Set(SYSTEM_INCLUDE_DIRECTORIES 
${SYSTEM_INCLUDE_DIRECTORIES}
${BASE_INCLUDE_DIRECTORIES}
)

set(INCLUDE_DIRECTORIES
${ROOT_INCLUDE_DIR} 
${BASE_INCLUDE_DIRECTORIES} 
#put here all directories where header files are located
${ENSARROOT_SOURCE_DIR}/sofia/base 
${ENSARROOT_SOURCE_DIR}/sofia/data/caloData
${ENSARROOT_SOURCE_DIR}/sofia/data/calData
${ENSARROOT_SOURCE_DIR}/sofia/data/landData 
${ENSARROOT_SOURCE_DIR}/sofia/data/twinmusicData
${ENSARROOT_SOURCE_DIR}/sofia/detectors/land
${ENSARROOT_SOURCE_DIR}/sofia/detectors/twinmusic 
${ENSARROOT_SOURCE_DIR}/sofia/mcstack 
${ENSARROOT_SOURCE_DIR}/sofia/passive 
)

include_directories( ${INCLUDE_DIRECTORIES})
include_directories(SYSTEM ${SYSTEM_INCLUDE_DIRECTORIES})

set(LINK_DIRECTORIES
${ROOT_LIBRARY_DIR}
${FAIRROOT_LIBRARY_DIR}
)
 
link_directories( ${LINK_DIRECTORIES})

set(SRCS
R3BGeoTwinMusic.cxx
R3BGeoTwinMusicPar.cxx
R3BTwinMusic.cxx
)

# fill list of header files from list of source files
# by exchanging the file extension
CHANGE_FILE_EXTENSION(*.cxx *.h HEADERS "${SRCS}")

set(LINKDEF TwinMusicLinkDef.h)
set(LIBRARY_NAME SOFIATwinMusic)
set(DEPENDENCIES
    Base FairTools GeoBase ParBase SOFIAbase SOFIAData)

GENERATE_LIBRARY()

include_directories(
    ${PROJECT_SOURCE_DIR}/src 
    ${PROJECT_BINARY_DIR}/src
	)

set(LIBRARIES)

### MANUAL_INCLUDE_DIRS is useful to force ides to find some includes (useless for compilation) ###
### To be used by editing the cache manually
include_directories(${MANUAL_INCLUDE_DIRS})

### OpenCV support ###
FIND_PACKAGE(OpenCV REQUIRED)
if(OpenCV_FOUND)
	include_directories(${OpenCV_INCLUDE_DIRS})
	set(LIBRARIES "${LIBRARIES}" "${OpenCV_LIBS}")
endif()
						
file(GLOB SRCS_FILES *.cpp)

add_executable(${PROJECT_NAME} ${SRCS_FILES}) 
# install(TARGETS freebalance DESTINATION ./)

### Linking ###
target_link_libraries(${PROJECT_NAME} ${LIBRARIES})
# Create a library called "libEGPythia6”

cmake_minimum_required(VERSION 3.15.7)

project(EGPythia6)

set(SRCS
src/TMCParticle.cxx
src/TPythia6.cxx
src/TPythia6Decayer.cxx
)

find_package(ROOT)

Set(LIBRARY_NAME EGPythia6)

add_library(${LIBRARY_NAME} SHARED ${SRCS})
target_include_directories(${LIBRARY_NAME} PUBLIC inc/)
target_link_libraries(${LIBRARY_NAME} ${PYTHIA6_ROOT}/lib/libpythia6.so ${PYTHIA6_ROOT}/lib/libPythia6.so)
target_link_libraries(${LIBRARY_NAME} ${ROOT_LIBRARIES})
target_link_libraries(${LIBRARY_NAME})
target_include_directories(${LIBRARY_NAME} PUBLIC ${ROOT_INCLUDE_DIRS})

ROOT_GENERATE_DICTIONARY(EGPythia6_dict inc/TMCParticle.h inc/TPythia6.h inc/TPythia6Decayer.h inc/TPythia6Calls.h MODULE EGPythia6 LINKDEF inc/LinkDef.h)

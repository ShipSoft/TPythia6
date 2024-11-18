# Create a library called "libtpythia6”

cmake_minimum_required(VERSION 3.15.7)

project(TPythia6)

set(SRCS
src/TMCParticle.cxx
src/TPythia6.cxx
src/TPythia6Decayer.cxx
)

find_package(ROOT)

Set(LIBRARY_NAME tpythia6)

add_library(${LIBRARY_NAME} SHARED ${SRCS})
target_include_directories(${LIBRARY_NAME} PUBLIC inc/)
target_link_libraries(${LIBRARY_NAME} ${PYTHIA6_ROOT}/lib/libpythia6.so ${PYTHIA6_ROOT}/lib/libPythia6.so)
target_link_libraries(${LIBRARY_NAME} ${ROOT_LIBRARIES})
target_link_libraries(${LIBRARY_NAME})
target_include_directories(${LIBRARY_NAME} PUBLIC ${ROOT_INCLUDE_DIRS})

ROOT_GENERATE_DICTIONARY(tpythia6_dict inc/TMCParticle.h inc/TPythia6.h inc/TPythia6Decayer.h inc/TPythia6Calls.h MODULE tpythia6 LINKDEF inc/LinkDef.h)

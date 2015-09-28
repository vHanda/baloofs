set(SRCS main.cpp)

add_executable(baloofs ${SRCS})
target_compile_definitions(baloofs PRIVATE -DPROJECT_VERSION="${PROJECT_VERSION}" ${FUSE_DEFINITIONS})

target_link_libraries(baloofs
   KF5::Baloo
   ${FUSE_LIBRARIES}
)

install(TARGETS baloofs DESTINATION ${BIN_INSTALL_DIR})

project( protoc )

include( ../protobuf-common.cmake )

set(SOURCES
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/main.cc
)

add_definitions(
  -D_CONSOLE
)

add_executable( protoc ${SOURCES} )
target_link_libraries( protoc libprotoc )
if( UNIX )
  if (NOT ANDROID)
    target_link_libraries( protoc -lpthread )
  endif()
endif()

install(TARGETS protoc
    RUNTIME DESTINATION ${BIN_DIR}
    )

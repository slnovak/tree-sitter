project(
  tree-sitter-lib
  VERSION 0.6.3
)

add_library(
  treesitter
  STATIC src/lib.c
)

target_include_directories(
  treesitter PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
  PRIVATE src
)

install(TARGETS treesitter EXPORT TreeSitterConfig
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
  LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

install(
  DIRECTORY include
  DESTINATION include ${CMAKE_INSTALL_INCLUDEDIR}
)

install(
  EXPORT TreeSitterConfig
  DESTINATION share/treesitter/cmake
)

export(
  TARGETS treesitter 
  FILE TreeSitterConfig.cmake
)

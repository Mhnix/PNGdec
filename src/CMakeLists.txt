add_library(PNGdec
  adler32.c
  crc32.c
  infback.c
  inffast.c
  inflate.c
  inftrees.c
  zutil.c
  PNGdec.cpp
)

set_target_properties(PNGdec PROPERTIES
  PUBLIC_HEADER
  PNGdec.h)
target_include_directories(PNGdec
                           INTERFACE
                            $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
                            $<INSTALL_INTERFACE:include>
                           )

target_compile_definitions(PNGdec PUBLIC NO_ARDUINO)
target_compile_options(PNGdec PRIVATE "-Wno-implicit-fallthrough")

install(FILES
  crc32.h
  inffast.h
  inffixed.h
  inflate.h
  inftrees.h
  zconf.h
  zlib.h
  zutil.h
  PNGdec.h
  DESTINATION include)

install(TARGETS PNGdec EXPORT PNGdec)

install(EXPORT PNGdec
  FILE PNGdecTargets.cmake
  NAMESPACE PNGdec::
  DESTINATION lib/cmake/PNGdec
)


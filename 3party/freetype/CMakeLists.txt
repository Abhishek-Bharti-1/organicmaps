set(FT_DISABLE_HARFBUZZ ON)

add_subdirectory(freetype)

# Fix warning with ONE_PIXEL macro clash.
target_compile_options(freetype PRIVATE -Wno-macro-redefined)

# Use ft2build.h from the current directory instead of the default.
target_include_directories(freetype
  BEFORE PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:include/freetype2>
)

add_library(Freetype::Freetype ALIAS freetype)


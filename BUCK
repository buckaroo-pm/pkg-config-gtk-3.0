pkg_config = read_config('pkg_config', 'path', 'pkg-config')

pkg_package = 'gtk+-3.0'

genrule(
  name = 'preprocessor-flags', 
  out = 'out.txt', 
  cmd = pkg_config + ' ' + pkg_package + ' --cflags > $OUT', 
)

genrule(
  name = 'linker-flags', 
  out = 'out.txt', 
  cmd = pkg_config + ' ' + pkg_package + ' --libs > $OUT', 
)

prebuilt_cxx_library(
  name = 'gtk-3.0', 
  header_namespace = '', 
  header_only = True, 
  exported_preprocessor_flags = [
    '@$(location :preprocessor-flags)', 
  ], 
  exported_linker_flags = [
    '@$(location :linker-flags)', 
  ], 
  visibility = [
    'PUBLIC', 
  ], 
)

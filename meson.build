project(
  'libresample',
  'c',
  version : '0.1.4',
  meson_version : '>=1.1',
  default_options : 'default_library=both',
)

cc = meson.get_compiler('c')

configure_file(
  output : 'config.h',
  configuration : {
    'HAVE_INTTYPES_H': cc.has_header('inttypes.h').to_int(),
  },
)
config_inc = include_directories('.')

libm_dep = cc.find_library('m', required : false)

resample = library(
  'resample',
  'src/filterkit.c',
  'src/resample.c',
  'src/resamplesubs.c',
  dependencies : [libm_dep],
  include_directories : [config_inc],
  version : meson.project_version(),
  soversion : 1,
  install : true,
)

install_headers('include/libresample.h')

pkg = import('pkgconfig')
pkg.generate(resample, name : 'libresample')

subdir('tests')

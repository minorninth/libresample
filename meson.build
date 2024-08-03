project(
  'libresample',
  'c',
  meson_version : '>=1.3',
  default_options : 'default_library=both',
  version : '0.1.5',
  license : 'BSD-3-Clause OR LGPL-2.1-or-later',
  license_files : ['LICENSE-BSD.txt', 'LICENSE-LGPL.txt'],
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
  vs_module_defs : 'src/resample.def',
  version : meson.project_version(),
  soversion : 1,
  install : true,
)

install_headers('include/libresample.h')

pkg = import('pkgconfig')
pkg.generate(resample, name : 'libresample')

subdir('tests')

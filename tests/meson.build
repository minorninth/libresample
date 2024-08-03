testresample = executable(
  'testresample',
  'testresample.c',
  dependencies : [libm_dep],
  link_with : [resample],
)
test('testresample', testresample)

sndfile_dep = dependency(
  'sndfile',
  required : get_option('resample-sndfile'),
)
if sndfile_dep.found()
  resample_sndfile = executable(
    'resample-sndfile',
    'resample-sndfile.c',
    dependencies : [sndfile_dep],
    link_with : [resample],
    install : true,
  )
endif

samplerate_dep = dependency(
  'samplerate',
  required : get_option('compareresample'),
)
if samplerate_dep.found()
  compareresample = executable(
    'compareresample',
    'compareresample.c',
    dependencies : [libm_dep, samplerate_dep],
    link_with : [resample],
    install : true,
  )
endif

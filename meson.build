project('argon2', 'c', version : '1')

version = meson.project_version()

legacy_meson = false

detect_meson_version = run_command('meson', '--version')
meson_ver = detect_meson_version.stdout()

if(meson_ver == '0.29.0\n')
  legacy_meson = true
elif(not meson.version().version_compare('>=0.40.0'))
  error('Meson 0.29.0 is last legacy version supported. Otherwise please upgrade to 0.40.0 or higher.')
endif

lib_src = ['src/argon2.c',
'src/bench.c',
'src/blake2/blake2-impl.h',
'src/blake2/blake2.h',
'src/blake2/blake2b.c',
'src/blake2/blamka-round-opt.h',
'src/blake2/blamka-round-ref.h',
'src/core.c',
'src/core.h',
'src/encoding.c',
'src/encoding.h',
'src/genkat.c',
'src/genkat.h',
'src/opt.c',
'src/ref.c',
'src/run.c',
'src/test.c',
'src/thread.c',
'src/thread.h']

inc = include_directories(['./include'])

lib = static_library('argon2', sources: lib_src, version: version,
include_directories: inc,
c_args: ['-Wall', '-Wno-unused-value', '-Wno-unused-function'],
install: true)

argon2_dep = declare_dependency(include_directories : inc, link_with : lib)

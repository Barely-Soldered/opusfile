project(
  'opusfile',
  'c',
  version: '0.12',
  license: 'BSD-3-Clause',
  meson_version: '>= 1.0.0',
  default_options: [
    'c_std=c99',
    'warning_level=1',
    'default_library=static',
  ],
)

ogg_dep = dependency('ogg')
opus_dep = dependency('opus')

opusfile_sources = files(
  'src/info.c',
  'src/internal.c',
  'src/opusfile.c',
  'src/stream.c',
)

opusfile_c_args = [
  '-DHAVE_CONFIG_H',
]

opusfile_internal_inc = include_directories('src', 'include/opus')
opusfile_public_inc = include_directories('include', is_system: true)

opusfile_lib = static_library(
  'opusfile',
  opusfile_sources,
  c_args: opusfile_c_args,
  include_directories: opusfile_internal_inc,
  dependencies: [ogg_dep, opus_dep],
)

opusfile_dep = declare_dependency(
  link_with: opusfile_lib,
  include_directories: opusfile_public_inc,
  dependencies: [ogg_dep, opus_dep],
)

meson.override_dependency('opusfile', opusfile_dep)

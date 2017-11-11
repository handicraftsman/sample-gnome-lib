add_global_arguments(
  ['-DGETTEXT_PACKAGE="sample"'],
  language: 'c'
)

libsrc = [
  'Foo.vala'
]

lib = shared_library(
  'gsample', # Library file name
  [
    # Sources.
    libsrc,

    # Configuration
    configure_file(
      input: 'config.in.vala',
      output: 'config.vala',
      configuration: conf
    )
  ],
  vala_args: [
    '--pkg', 'posix',
    '--shared-library', 'libgsample'
  ], # Required for Posix namespace
  dependencies: global_dependencies + [
    # dependency('gtk-3.0') # A sample local dependency
  ],

  vala_header: 'gsample.h',
  vala_vapi: 'gsample-0.vapi',
  vala_gir: 'GSample-0.gir',
  install: true,
  install_dir: [true, true, true, true]
)

pkg.generate(
  requires: ['glib-2.0', 'gio-2.0'],
  libraries: ['-lgsample'],
  name: 'gsample-0', 
  version: conf.get('version'),
  description: 'A sample library'
)

custom_target(
  'gsample typelib',
  command: [
    find_program('g-ir-compiler'),
    '--shared-library', lib.full_path(),
    '--output', '@OUTPUT@',
    join_paths(meson.current_build_dir(), 'GSample-0.gir')
  ],
  output: 'GSample-0.typelib',
  depends: lib,
  install: true,
  install_dir: join_paths(get_option('libdir'), 'girepository-1.0')
)
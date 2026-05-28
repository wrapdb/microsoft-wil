custom_target(
  'docs',
  command: [doxygen_exe, '@INPUT@'],
  input: 'Doxyfile',
  depend_files: nosal2_doxyfile,
  output: 'html',
  env: {
    'DOXYGEN_OUTPUT_DIRECTORY': meson.current_build_dir(),
    'WIL_BUILD_VERSION': meson.project_version(),
  },
  build_by_default: false,
  install: true,
  install_dir: get_option('datadir') / 'doc' / meson.project_name(),
  install_tag: 'doc',
)

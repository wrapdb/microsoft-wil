# SPDX-License-Identifier: 0BSD
# SPDX-FileCopyrightText: (C) 2026 Zephyr Lykos <self@mochaa.ws>

project(
  'msft_wil',
  version: '1.0.260114.1',
  meson_version: '>= 1.3.0',
  default_options: ['warning_level=3'],
)

wil_srcs = files(
  'include/wil/Tracelogging.h',
  'include/wil/com.h',
  'include/wil/com_apartment_variable.h',
  'include/wil/common.h',
  'include/wil/coroutine.h',
  'include/wil/cppwinrt.h',
  'include/wil/cppwinrt_authoring.h',
  'include/wil/cppwinrt_helpers.h',
  'include/wil/cppwinrt_notifiable_server_lock.h',
  'include/wil/cppwinrt_wrl.h',
  'include/wil/filesystem.h',
  'include/wil/network.h',
  'include/wil/nt_result_macros.h',
  'include/wil/registry.h',
  'include/wil/registry_helpers.h',
  'include/wil/resource.h',
  'include/wil/result.h',
  'include/wil/result_macros.h',
  'include/wil/result_originate.h',
  'include/wil/rpc_helpers.h',
  'include/wil/safecast.h',
  'include/wil/stl.h',
  'include/wil/token_helpers.h',
  'include/wil/traceloggingconfig.h',
  'include/wil/win32_helpers.h',
  'include/wil/win32_result_macros.h',
  'include/wil/windowing.h',
  'include/wil/winrt.h',
  'include/wil/wistd_config.h',
  'include/wil/wistd_functional.h',
  'include/wil/wistd_memory.h',
  'include/wil/wistd_type_traits.h',
  'include/wil/wrl.h',
)
wil_inc = include_directories('include')
wil_dep = declare_dependency(
  include_directories: wil_inc,
)
meson.override_dependency(meson.project_name(), wil_dep)

install_headers(
  wil_srcs,
  subdir: 'wil',
)

pkgconfig = import(
  'pkgconfig',
  required: false,
)
if pkgconfig.found()
  pkgconfig.generate(
    name: meson.project_name(),
    description: 'Windows Implementation Library',
    url: 'https://github.com/microsoft/wil',
    dataonly: true,
  )
endif

docs = get_option('docs').disable_auto_if(meson.is_subproject())
doxygen_exe = find_program('doxygen', required: docs)
if doxygen_exe.found()
  nosal2_doxyfile = configure_file(input: 'docs/nosal2.doxyfile', output: 'nosal2.doxyfile', copy: true)
endif
subdir('docs', if_found: doxygen_exe)

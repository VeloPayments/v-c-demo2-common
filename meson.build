project('vcdemo2common', 'c', 'cpp',
  version : '0.4.1',
  default_options : ['c_std=gnu11', 'cpp_std=c++14', 'buildtype=release'],
  meson_version : '>=0.53.0'
)

message('Using build type: ' + get_option('buildtype'))

force_velo_toolchain = get_option('force_velo_toolchain')

if force_velo_toolchain
  cc = meson.get_compiler('c')
  cc_version = run_command(cc.cmd_array() + ['--version'], check : true).stdout()
  if not cc_version.contains('(velo)')
    error('force_velo_toolchain is set and you arn\'t using the velo toolchain.')
  endif
  cpp = meson.get_compiler('cpp')
  cpp_version = run_command(cpp.cmd_array() + ['--version'], check : true).stdout()
  if not cpp_version.contains('(velo)')
    error('force_velo_toolchain is set and you arn\'t using the velo toolchain.')
  endif
else
  warning('Not using the blessed velo gcc toolchain. Here be dragons.')
endif

add_project_arguments('-Wall', '-Werror', '-Wextra', language : 'c')
add_project_arguments('-Wall', '-Werror', '-Wextra', language : 'cpp')

src = run_command('find', './src', '-name', '*.c', check : true).stdout().strip().split('\n')
test_src = run_command('find', './test', '-name', '*.cpp', check : true).stdout().strip().split('\n')

vcblockchain = dependency(
    'vcblockchain',
    required : true,
    fallback : ['vcblockchain', 'vcblockchain_dep']
)

cmake = import('cmake')
minunit_proj = cmake.subproject('minunit')
minunit = minunit_proj.dependency('minunit')

vcdemo2common_include = include_directories('include')

vcdemo2common_lib = static_library('vcdemo2common', src,
  src,
  dependencies : [vcblockchain],
  include_directories: vcdemo2common_include,
)

vcdemo2common_test = executable(
    'vcdemo2common-test',
    src, test_src,
    include_directories : vcdemo2common_include,
    dependencies : [vcblockchain, minunit]
)

test(
    'vcdemo2common_test',
    vcdemo2common_test,
)

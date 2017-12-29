project('MUMPS', ['c', 'fortran'], version:'5.1.2')

cc = meson.get_compiler('c')

LAPACK_dep = meson.superproject().get_variable('LAPACK_dep')
if not LAPACK_dep.found()
  LAPACK_dep = subproject('coinlapack').get_variable('coinlapack_dep')
endif

add_project_arguments('-DAdd_', '-DMUMPS_ARITH=MUMPS_ARITH_d', language: 'c')
# FIXME other fortran standard libraries
fortran_lib = cc.find_library('gfortran')
threads_dep = dependency('threads')

coinmumps_libs = []
subdir('libseq')
subdir('src')

coinmumps_dep = declare_dependency(link_with: coinmumps_libs,
                                   dependencies: [fortran_lib, threads_dep, LAPACK_dep],
                                   include_directories: include_directories('libseq', 'include'))

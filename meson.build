project('MUMPS', ['c', 'fortran'], version:'5.1.2')

LAPACK_dep = subproject('LAPACK').get_variable('coinlapack_dep')

add_project_arguments('-DAdd_', '-DMUMPS_ARITH=MUMPS_ARITH_d', language: 'c')
# FIXME other fortran standard libraries
fortran_lib = meson.get_compiler('c').find_library('gfortran')
threads_dep = dependency('threads')

coinmumps_libs = []
subdir('libseq')
subdir('src')

coinmumps_dep = declare_dependency(link_with: coinmumps_libs,
                                   dependencies: [fortran_lib, threads_dep, LAPACK_dep],
                                   include_directories: include_directories('libseq', 'include'))

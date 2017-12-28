headers = [
  'mpi.h'
]
install_headers(headers, subdir: 'coin/ThirdParty')

sources = [
  'mpi.f',
  'mpic.c',
  'elapse.c'
]

libmumpsmpi_seq = static_library('mumpsmpi_seq', sources,
                                 include_directories: include_directories('.'),
                                 install: false)
coinmumps_libs += [libmumpsmpi_seq]

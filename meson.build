project('snowtools-crps', 'c',
   version: '0.1',
   default_options: [
    'c_std=c99'
  ],
  )

py = import('python').find_installation(pure: false)


add_languages('fortran')

incdir_numpy = run_command(py,
  ['-c', 'import os; os.chdir(".."); import numpy; print(numpy.get_include())'],
  check : true
 ).stdout().strip()

 incdir_f2py = run_command(py,
    ['-c', 'import os; os.chdir(".."); import numpy.f2py; print(numpy.f2py.get_include())'],
    check : true
).stdout().strip()

crps_source = custom_target('crpsmodule.c',
  input : ['./src/crps.f90'],
  output : 'crpsmodule.c',
  command : [py, '-m', 'numpy.f2py', '@INPUT@', '-m', 'crps', '--lower'],
)

inc_np = include_directories(incdir_numpy, incdir_f2py)

py.extension_module(
   'crps',
   ['./src/crps.f90', crps_source],
   incdir_f2py / 'fortranobject.c',
    include_directories: inc_np,
    install: true,
)


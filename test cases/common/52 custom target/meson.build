project('custom target', 'c')

python = find_program('python3', required : false)
if not python.found()
  python = find_program('python')
endif

# Note that this will not add a dependency to the compiler executable.
# Code will not be rebuilt if it changes.
comp = '@0@/@1@'.format(meson.current_source_dir(), 'my_compiler.py')
# Test that files() in command: works. The compiler just discards it.
useless = files('installed_files.txt')

mytarget = custom_target('bindat',
output : 'data.dat',
input : 'data_source.txt',
command : [python, comp, '--input=@INPUT@', '--output=@OUTPUT@', useless],
install : true,
install_dir : 'subdir'
)

has_not_changed = false
if is_disabler(mytarget)
    has_not_changed = true
else
    has_not_changed = true
endif
assert(has_not_changed, 'Custom target has changed.')

assert(not is_disabler(mytarget), 'Custom target is a disabler.')

subdir('depfile')

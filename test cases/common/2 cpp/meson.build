project('c++ test', 'cpp')

cpp = meson.get_compiler('cpp')
if cpp.get_id() == 'intel'
  # Error out if the -std=xxx option is incorrect
  add_project_arguments('-diag-error', '10159', language : 'cpp')
elif cpp.get_id() == 'intel-cl'
  add_project_arguments('/Qdiag-error:10159', language : 'cpp')
endif

exe = executable('trivialprog', 'trivial.cc', extra_files : 'something.txt')
test('runtest', exe)

has_not_changed = false
if is_disabler(exe)
    has_not_changed = true
else
    has_not_changed = true
endif
assert(has_not_changed, 'Executable has changed.')

assert(not is_disabler(exe), 'Executable is a disabler.')

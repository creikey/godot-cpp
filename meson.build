project('godot-cpp', 'cpp')

gen_script = find_program('binding_generator.py', native : true)
gen_return = run_command(gen_script, get_option('api_json_path'), '@0@'.format(get_option('force_regen_bindings')))

if gen_return.returncode() != 0
  message('failed to generate bindings')
endif

sources = []
subdir('src/gen')
subdir('src/core')

inc = include_directories('include', 'include/core', 'include/gen', 'godot_headers')
lib = static_library('godot-cpp', 
  sources,
  include_directories : inc,
  pic : true)

lib_dep = declare_dependency(include_directories : inc,
  link_with : lib)

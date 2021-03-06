project('SampleLib', ['c', 'vala'], version: '0.1.0')
'''
Name `SampleApp` is a placeholder for your app name.
In this example app version will always be 0.1.0.
When writing vala apps you need to have c compiler too,
so you should require it in `project` function.
'''

'''
You must import 'gnome' to use GNOME-related features
(except for pkg-config).
'''
gnome = import('gnome')
pkg = import('pkgconfig')

'''
`configuration_data()` is used to setup application config
so it can be used in your meson.build files and application
files

Chose your app id and path using this guide: https://developer.gnome.org/ChooseApplicationID/
'''
conf = configuration_data()
conf.set('name', meson.project_name())
conf.set('version', meson.project_version())

'''
Change this array to set global dependencies.
`dependency()` function supports pkg-config, boost, qt and
other tools/libraries.
'''
global_dependencies = [
  dependency('glib-2.0', version: '>=2.40'),
  dependency('gio-2.0', version: '>=2.40')
]

'''
`subdir(dir)` function basically executes `dir/meson.build`
file in current VM state. This means that variables and targets
defined in main file will be available in ALL subdir files.
All build artifacts build by targets defined in subdir will be
available in `/build/dir/` directory.

Feel free to comment/delete subdir() calls below if you do not
need them - this setup is designed to be fully modular
'''
subdir('src') # A source directory for `sample` executable

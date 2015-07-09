# SublimePythonTestRunner

This [Sublime Text](http://www.sublimetext.com/) plugin allows python users to run tests quickly from within a project environment.

## Usage

The simplest usage is simply running the build system; `super+shift+b` and select `Python Test Runner` from the build system selection dropdown, after using it once you may hit `super+b` to run the default build system. You may also run a specified test class or function by selecting the desired test prior to running test (`{selection}` placeholder is replaced in `cmd` by the selected test).

## Configuration

By default the command we run is `py.test -k {selection} ${file}`, but you may customize the command in your `project.sublime-project` settings. For example Django's test runner can be run like so:

```json
{
    "build_systems":
    [
        {
            "cmd":
            [
                "python",
                "manage.py",
                "test",
                "--noinput",
                "${file}:{selection}",
                "--settings=test_settings"
            ],
            "env":
            {
                "PYTHONPATH": "/home/user/.venvs/project/lib/python2.7/site-packages",
                "REUSE_DB": "1"
            },
            "name": "Django Test",
            "target": "python_test_runner",
            "working_dir": "${project_path}/project/"
        }
    ]
}
```

For more info on the SublimeText build-system configuration see [the unofficial documentation](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/reference/build_systems/configuration.html).

## Sublime ANSI

This plugin supports passing the command through [ANSIescape](https://github.com/aziz/SublimeANSI) to display ANSI colors in the ST output panel. This will be automatically activated if the plugin is installed.

# Fortran Breakpoint Support

Add breakpoint support for fortran

## Features

![feature X](https://github.com/ekibun/FortranBreaker/blob/master/screenshot.png?raw=true)

## Requirements

* `Gimly81.fortran` or `krvajalm.linter-gfortran`
* `ms-vscode.cpptools`

## Usage

**Windows :**
* Install MINGW-W64 (or other debugger) and all above extensions
* Add `.vscode/launch.json` to project.  An example:

```json
{
    "version": "0.0.1",
    "configurations": [
        {
            "name": "Fortran Launch (GDB)",
            "type": "cppdbg",
            "request": "launch",
            "targetArchitecture": "x86",
            "program": "${workspaceRoot}\\${fileBasenameNoExtension}.exe",
            "miDebuggerPath": "gdb.exe",
            "args": [], 
            "stopAtEntry": false,
            "cwd": "${workspaceRoot}",
            "externalConsole": true,
            "preLaunchTask": "gfortran"
        },
        {
            "name": "Intel Debug Attach",
            "type": "cppvsdbg",
            "request": "attach",
            "processId": "${command:pickProcess}"
        }
    ]
}
```

* Add a build command to `tasks.json`.  An example:

```json
{
    "version": "0.0.1",
    "command": "gfortran",
    "args": [
        "-g",
        "${file}",
        "-o",
        "${workspaceRoot}\\${fileBasenameNoExtension}.exe"
    ]
}
```

**Linux :**
* Make sure gdb is working with `gdb -v`
* Add `.vscode/launch.json` to project.  An example:
```json
{
    "version" : "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Fortran",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/${fileBasenameNoExtension}.out",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "preLaunchTask": "gfortran",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": false
                }
                
            ]
        }
    ]
}
```
* Add a build command to `tasks.json`.  An example:
```json
{
    "version": "0.0.1",
    "command": "gfortran",
    "args": [
        "-g",
        "${file}",
        "-o",
        "${workspaceFolder}/${fileBasenameNoExtension}.out"
    ]
}
```
## Release Notes

## 0.0.4

Enable breakpoints for MSVC and support for krvajalm.linter-gfortran by [emanspeaks](https://github.com/emanspeaks)

### 0.0.3

Enable breakpoints for Fortran - Modern by [letmaik](https://github.com/letmaik)

### 0.0.2

Add icon and usage

### 0.0.1

Initial release

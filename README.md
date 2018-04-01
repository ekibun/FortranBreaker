# Fortran Breakpoint Support 

Add breakpoint support for fortran

## Features

![feature X](https://github.com/ekibun/FortranBreaker/blob/master/screenshot.png?raw=true)

## Requirements

> Gimly81.fortran

> ms-vscode.cpptools

## Usage

1. Install MINGW-W64 and all above extensions
2. Add ```.vscode``` folder
3. Add ```launch.json```
```
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
        }
    ]
}
```
4. Add ```tasks.json```
```
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

## Release Notes

### 0.0.2

Add icon and usage

### 0.0.1

Initial release
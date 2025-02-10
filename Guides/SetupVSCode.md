# VSCode for Stockfish and derivative

## 1. Install VSCode

### 1.1 Linux as a snap package

```bash
sudo snap install --classic code
```

### 1.2 Windows

You can find the installer online at [this link](code.visualstudio.com/Download).

### 2. Install the official c++ extensions by Microsoft

### 3. Open the folder with the src

### 4. Create the tasks.json file:

Create a new file named 'tasks.json' in the '.vscode' folder within your project directory. If the '.vscode' folder doesn't exist, you can create it.

Then add the following configuration to the 'tasks.json' file to build the Stockfish project with G++ and generate debugging information:

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Custom Build",
            "type": "process",
            "command": "${env:COMSPEC}",
            "args": ["/c", "C:/git/ShashChess/src/build.bat"],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": [],
            "presentation": {
                "reveal": "always",
                "panel": "shared"
            }
        }
    ]
}
```

Run the project by pressing 'Ctrl+Shift+B' in VSCode, which will execute the build task defined in the 'tasks.json' file.

Change debug=no to debug=yes and optimize=no to optimize=yes

Remaining in the '.vscode' folder, create the file 'launch.json' with the following content:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug with GDB",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/shashchess.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "Custom Build",
            "miDebuggerPath": "C:/tools/msys64/mingw64/bin/gdb.exe",
            "miDebuggerArgs": "",
            "showDisplayString": true
        }
    ]
}
```

Finally press F5 to debug the code (breakpoints, etc)

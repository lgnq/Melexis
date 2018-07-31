# Melexis TPMS development environment [VSCode]  
## install Melexis GCC Compiler  
download [Melexis GCC Compiler](https://softdist.melexis.com)
## install Visual Studio Code  
download [Visual Studio Code](https://code.visualstudio.com/Download)
## configure Visual Studio Code  
### install extensions  
install Microsoft C/C++ for Visual Studio Code
### add tasks  
1. edit tasks.json  
```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format

    "version": "2.0.0",
    "tasks": [
        // add tasks here
    ]
}
```  
2. add task "make all"  
```
        {
            "label": "make all",
            "type": "shell",
            "command": "make",
            "options": {
                "cwd": "${fileDirname}"
            },
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "args": [
                "all", "-j4"
            ],
            "presentation": {
                "reveal": "always",
                "panel": "new"
            },
            "problemMatcher": {
                "owner": "c",
                "fileLocation": [
                    "relative",
                    "${workspaceFolder}"
                ],
                "pattern": {
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning|error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        },
```        
3. add task "make clean"  
```
        {
            "label": "make clean",
            "type": "shell",
            "command": "make",
            "options": {
                "cwd": "${fileDirname}"
            },
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "args": [
                "clean"
            ],
            "problemMatcher": []
        },
```        
4. add task "make clean_libs"  
```
        {
            "label": "make clean_libs",
            "type": "shell",
            "command": "make",
            "options": {
                "cwd": "${fileDirname}"
            },
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "args": [
                "clean_libs"
            ],
            "problemMatcher": []
        },
```        
### configure shortcuts   
Keyboard Shortcuts -> keybindings.json  

```
[
    { 
        "key": "F8", 
        "command": "workbench.action.tasks.runTask",
        "args": "make all"
    },
    { 
        "key": "F7", 
        "command": "workbench.action.tasks.runTask",
        "args": "make clean"
    },
    { 
        "key": "F6", 
        "command": "workbench.action.tasks.runTask",
        "args": "make clean_libs"
    },
]
```  
### shortcuts for VSCode  
enter command : Ctrl+Shift+P   
open/close terminal : Ctrl+`    
open/close Explorer : Ctrl+B


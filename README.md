# cpp-checker

[![GitHub release](https://img.shields.io/github/release/bubble5144/cpp-checker-misra.svg?style=plastic)](https://github.com/bubble5144/cpp-checker-misra/releases)
[![GitHub license](https://img.shields.io/github/license/bubble5144/cpp-checker-misra.svg?style=plastic)](https://github.com/bubble5144/cpp-checker-misra/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/bubble5144/cpp-checker-misra?style=plastic)](https://github.com/bubble5144/cpp-checker-misra/stargazers)
[![GitHub fork](https://img.shields.io/github/forks/bubble5144/cpp-checker-misra.svg?style=plastic)](https://github.com/bubble5144/cpp-checker-misra/network/members)
[![GitHub issues](https://img.shields.io/github/issues/bubble5144/cpp-checker-misra.svg?style=plastic)](https://github.com/bubble5144/cpp-checker-misra/issues)

A fork of [cpp-check-lint by QiuminGe](https://github.com/QiuminGe/cpp-check-lint)

## Features

 * cppcheck/cpplint:
    * editor/context      
        * check current file    
        * check the directory of the current file    
        * cmd :    
            * clear all    
            * clear current file    
            * stop check    
    * explorer/context
        * check directory || check current file
        * cmd  
    * OnSave/QuickFix

## Requirements

### cppcheck
* Install from source
    ```
    http://cppcheck.net/
    ```
* Install for yum/apt_get/brew : 
    ```
    sudo apt-get install cppcheck
    sudo yum install cppcheck
    brew install cppcheck
    ```
* help    
   http://cppcheck.sourceforge.net/manual.html

### cpplint

* Install from source
    ```
    https://github.com/cpplint/cpplint
    ```
* Install from pip
    ```
    pip install cpplint
    ```

### builtin binaries

* cppcheck 2.4.1
* cpplint 1.5.5

    > support  (**linux cpplint need python**)
    >> | Os | Bit | Version | 
    >> |:--:|:---:|:--------|
    >> |Ubuntu|64|16.04+|
    >> |Debian|64|9+|
    >> |CentOS|64|7+|
    >> |RHEL|64|7+|
    >> |Windows|64|7+|

## Extension Settings

 * Cppcheck:--executable   
    ``` 
    if (cppcheck configure is null) {
        use builtin binaries
    } else {
        if( ("path to executable" --version).trim().toLowerCase().startsWith("cppcheck") ){
            use "path to executable"
        } else {
        use builtin binaries 
        }
    }
    ```
 * Cppcheck:--addon= 

    ```json
    [
        "cert", 
        {
            "script": "misra.py", 
            "args": [
                "--rule-texts=/home/user/misra.txt"
            ]
        }, 
        "y2038.py", 
        "C:\\UsersAdministrator\\hreadsafety.json"
    ]
    ```
    "addon" and "addon.py" will use addons folder under the same level folder as cppcheck . 

    ```
    [rorot@cpppcheck]$ tree | grep -E " cppcheck.exe| addons| misra.py| y2038.py| cert.py| threadsafety.py"
    ├── addons
    │   ├── cert.py
    │   ├── misra.py
    │   ├── threadsafety.py
    │   └── y2038.py
    ├── cppcheck.exe
    ```
     Some addons need extra arguments. You can configure json or json file.
    ```
    {
        "script": "misra.py",
        "args": [
            "--rule-texts=/home/user/misra.txt"
        ]
    }
    "--rule-texts=/home/user/misra.txt" (need absolute path, and use "/" or "\\" to split paths)
    If ${workspace folder} is included, it will be replaced.
    "args": ["--rule-texts=${workspaceFolder}/rule/misra.txt"] -> "args":["--rule-texts=D:/code/demo/rule/misra.txt"]}
    ```
*  Cpplint:--executable
    ```
    if (cpplint configure is null) {
        use builtin binaries
    } else {
        if("path to executable"){
            use "path to executable"
        } else {
            use builtin binaries 
        }
    } 
    ```
* Cpplint:--recursive
* Cpplint:--lintdir
    ``` 
    if ( cpplint version support "--recursive") {
            set --recursive true
        } else {
            set "--recursive" false
            set "--lintdir"
    }
    ``` 

* customargs

    If the configuration parameters cannot be satisfied, use custom configuration "--customargs="

* OnSave

    cpplint suggest use with clang-format

* QuickFix

    It's just suppresses alarms

* Configure
    > skip unsupported flag
    >> | type | value | 
    >> |:----:|:-----:|
    >> |bool|false|
    >> |string|""|
    >> |number|null|
    >> |object|null|

## Known Issues

* cpp-checker https://github.com/bubble5144/cpp-checker-misra/issues

* cpplint : https://github.com/cpplint/cpplint/issues

* cppcheck : https://sourceforge.net/p/cppcheck/wiki/Home/

## Source code 

* https://github.com/bubble5144/cpp-checker-misra

##  [Release Notes](https://github.com/bubble5144/cpp-checker-misra/blob/main/CHANGELOG.md)

-----------------------------------------------------------------------------------------------------------


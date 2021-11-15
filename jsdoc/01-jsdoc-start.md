# 시작하기
## 설치하기

Vue 관련 URL 

[https://storybook.js.org/tutorials/intro-to-storybook/vue/en/get-started/](https://storybook.js.org/tutorials/intro-to-storybook/vue/en/get-started/)

```jsx
# Clone the template
npx degit chromaui/intro-storybook-vue-template taskbox

cd taskbox

# Install dependencies
yarn
```

> 설치하다가 에러남.   python 최신 버전 설치하라고 나옴
> 

```jsx
gyp ERR! find Python - "C:\Program Files\Python36\python.exe" could not be run
gyp ERR! find Python checking if Python is C:\Users\latte\AppData\Local\Programs\Python\Python36-32\python.exe
gyp ERR! find Python - "C:\Users\latte\AppData\Local\Programs\Python\Python36-32\python.exe" could not be run
gyp ERR! find Python checking if Python is C:\Program Files\Python36-32\python.exe
gyp ERR! find Python - "C:\Program Files\Python36-32\python.exe" could not be run
gyp ERR! find Python checking if Python is C:\Program Files (x86)\Python36-32\python.exe
gyp ERR! find Python - "C:\Program Files (x86)\Python36-32\python.exe" could not be run
gyp ERR! find Python checking if the py launcher can be used to find Python 3
gyp ERR! find Python - "py.exe" is not in PATH or produced an error
gyp ERR! find Python
gyp ERR! find Python **********************************************************
gyp ERR! find Python You need to install the latest version of Python.
gyp ERR! find Python Node-gyp should be able to find and use Python. If not,
gyp ERR! find Python you can try one of the following options:
gyp ERR! find Python - Use the switch --python="C:\Path\To\python.exe"
gyp ERR! find Python   (accepted by both node-gyp and npm)
gyp ERR! find Python - Set the environment variable PYTHON
gyp ERR! find Python - Set the npm configuration variable python:
gyp ERR! find Python   npm config set python "C:\Path\To\python.exe"
gyp ERR! find Python For more information consult the documentation at:
gyp ERR! find Python https://github.com/nodejs/node-gyp#installation
gyp ERR! find Python **********************************************************
gyp ERR! find Python
gyp ERR! configure error
gyp ERR! stack Error: Could not find any Python installation to use
gyp ERR! stack     at PythonFinder.fail (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-python.js:330:47)
gyp ERR! stack     at PythonFinder.runChecks (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-python.js:159:21)
gyp ERR! stack     at PythonFinder.<anonymous> (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-python.js:228:18)
gyp ERR! stack     at PythonFinder.execFileCallback (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-python.js:294:16)
gyp ERR! stack     at exithandler (node:child_process:404:5)
gyp ERR! stack     at ChildProcess.errorhandler (node:child_process:416:5)
gyp ERR! stack     at ChildProcess.emit (node:events:390:28)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (node:internal/child_process:288:12)
gyp ERR! stack     at onErrorNT (node:internal/child_process:477:16)
gyp ERR! stack     at processTicksAndRejections (node:internal/process/task_queues:83:21)
gyp ERR! System Windows_NT 10.0.22000
gyp ERR! command "C:\\Program Files\\nodejs\\node.exe" "C:\\Program Files\\nodejs\\node_modules\\npm\\node_modules\\node-gyp\\bin\\node-gyp.js" "rebuild"        
gyp ERR! cwd G:\github\html5\storybook\taskbox\node_modules\deasync
gyp ERR! node -v v16.11.1
```

```jsx
gyp ERR! find VS not looking for VS2013 as it is only supported up to Node.js 8
gyp ERR! find VS
gyp ERR! find VS **************************************************************
gyp ERR! find VS You need to install the latest version of Visual Studio
gyp ERR! find VS including the "Desktop development with C++" workload.
gyp ERR! find VS For more information consult the documentation at:
gyp ERR! find VS https://github.com/nodejs/node-gyp#on-windows
gyp ERR! find VS **************************************************************
gyp ERR! find VS
gyp ERR! configure error
gyp ERR! stack Error: Could not find any Visual Studio installation to use
gyp ERR! stack     at VisualStudioFinder.fail (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-visualstudio.js:121:47)
gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-visualstudio.js:74:16
gyp ERR! stack     at VisualStudioFinder.findVisualStudio2013 (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-visualstudio.js:351:14)   
gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-visualstudio.js:70:14
gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\find-visualstudio.js:372:16
gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\util.js:54:7
gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\util.js:33:16
gyp ERR! stack     at ChildProcess.exithandler (node:child_process:404:5)
gyp ERR! stack     at ChildProcess.emit (node:events:390:28)
gyp ERR! stack     at maybeClose (node:internal/child_process:1064:16)
gyp ERR! System Windows_NT 10.0.22000
gyp ERR! command "C:\\Program Files\\nodejs\\node.exe" "C:\\Program Files\\nodejs\\node_modules\\npm\\node_modules\\node-gyp\\bin\\node-gyp.js" "rebuild"        
gyp ERR! cwd G:\github\html5\storybook\taskbox\node_modules\deasync
gyp ERR! node -v v16.11.1
```

아래 사이트에 가니 Visual C++ Build tool을 설치하라고 나온다.

[https://github.com/nodejs/node-gyp#on-windows](https://github.com/nodejs/node-gyp#on-windows)

```jsx
On Windows
Install the current version of Python from the Microsoft Store package.

Install tools and configuration manually:

Install Visual C++ Build Environment: Visual Studio Build Tools (using "Visual C++ build tools" workload) or Visual Studio Community (using the "Desktop development with C++" workload)
Launch cmd, npm config set msvs_version 2017
```
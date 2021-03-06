Sublime-IJulia
======

Successor to the Sublime-Julia project, now based on the IJulia backend.

Julia is a new, open-source technical computing language built for speed and simplicity. The IJulia project
built an IPython kernel for Julia to provide the typical IPython frontend-backend functionality such as
the popular notebook, qtconsole, and regular terminal. 

Sublime-IJulia builds on these efforts by providing a frontend to the IJulia backend kernel. All within Sublime, 
a user can start up an IJulia frontend in a Sublime view and interact with the kernel. This allows for rapid 
code development through REPL testing and debugging without ever having to leave our favorite editor.

This project is still in beta, so please be patient and open [issues](https://github.com/karbarcca/Sublime-IJulia/issues) liberally.

#### IJulia Installation
Before installing the Sublime-IJulia package, you must first ensure you have added and successfully built the IJulia package from within julia itself. This can be done by running:
```julia
Pkg.add("IJulia")
```
The package has built successfully if you don't see any errors. See the [IJulia](https://github.com/JuliaLang/IJulia.jl) page for additional help.


#### Sublime-IJulia Installation
1. Within Sublime Text 3, install the Package Control package from [here](https://sublime.wbond.net/installation)
2. With Package Control successfully installed, run `Ctrl+Shift+p` (`Cmd+Shift+p` on OSX) to open the Sublime command pallette and start typing "Install Package", then select "Package Control: Install Package".
3. From the list of packages that are then shown, start typing "IJulia" and then select the "IJulia" package. This installs the IJulia package into your Sublime packages directory.
4. From the menu bar, open `Preferences => Package Settings => Sublime-IJulia => Settings - Default`
5. Then, from the menu bar, open `Preferences => Package Settings => Sublime-IJulia => Settings - User`
6. Copy everything from the `Settings - Default` file into the `Settings - User` file
7. Now, in the `Settings - User` file, change the value of the `julia_command` field to the absolute path to your julia executable. If julia is on your path, this may not involve changing anything (i.e if you can type `julia` from the command line from any directory). Otherwise, under your appropriate system, unix => OSX, Linux, windows => Windows, puth the full path to your julia executable (i.e. `/usr/home/julia/usr/bin/julia`).
8. On Windows and Linux, you should *not* have to change the `zmq_shared_library` field value. These are (fairly) standard installation locations, so they should work out of the box. For OSX, the default value is a best guess, but the value is subject to change depending on where homebrew ends up installing the ZMQ library when building the IJulia package from within julia. The easiest way to locate your ZMQ library (on any platform) is to to run the following commands from within julia: `using ZMQ; ZMQ.zmq`
9. With the two values properly set in the settings file, you can now run `Ctrl+Shift+p` to open the command pallette and start typing "Open IJulia" and select "Sublime-IJulia: Open New IJulia Console". If all goes well, a new view should open up in Sublime, titled `*IJulia 0*` and the julia banner should display shortly (2-5 seconds). Success!
10. If an error message pops up, the new view doesn't open, or nothing shows up in your new view, there's been some kind of error in the above steps. Please go back over the steps to ensure everything was followed and if the results are the same, please open an issue [here](https://github.com/karbarcca/Sublime-IJulia/issues) and I'm more than happy to help troubleshoot the installation.

#### Using Sublime-IJulia
* Commands can be entered directly in the IJulia console view, pressing `enter` to execute. 
* A newline can be entered without executing the command by typing `Shift+Enter` for multi-line commands.
* Pressing the `up` and `down` arrows in the console view will navigate through command history (if any).
* `escape` will clear the current command
* All other regular sublime features should work as normal also in the console view (multiple cursors, macros, etc.)


From a julia file (extension .jl), you also have the ability to "send" code to the console to be evaluated. 
* `Ctrl+enter` without any code selected will send the current line to the console to be executed
* `Ctrl+enter` with code selected will send the selected text to the console to be executed
* `Ctrl+shift+enter` will send the entire file's contents to the console to be executed

#### Other Sublime-IJulia Package Features
* Auto-completion: Most of the [stdlib](http://docs.julialang.org/en/latest/stdlib/base/#) julia functions can be auto-completed from the console and julia (.jl) files. Just start typeing a function name and press `tab` to auto-complete with the expected arguments.
* Syntax: Syntax highlighting is available for julia files (.jl), you can set them manually by clicking in the lower right-hand side of sublime (there will be "Text" or some other language displayed) and select "Julia" from the list
* You can also automatically apply the Julia syntax by typing `Ctrl+Shift+p` and start typing "Apply Julia syntax" and select that command. This will automatically apply the Julia syntax to all open (.jl) files.
* Build: A basic build file is provided, but will probably have to be manually tweaked to provide the path to your julia executable. This can be done by opening your Sublime packages folder, going to the IJulia directory and opening the `julia-build.sublime-build` file.


Cheers!

-Jacob Quinn

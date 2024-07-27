# FNA VSCode Template
Start new FNA projects quickly and easily with handy setup scripts, a versatile boilerplate project, and convenient Visual Studio Code integration.

## Features ##
- Super simple setup scripts that download and install FNA and its native libraries for you!
- Boilerplate project already included -- no need to wrestle with MSBuild configurations or writing yet another Game1 class.
- Visual Studio Code tasks for building and running your game, cleaning/restoring your project, and compiling .fx files!
- In-editor debugging support with the Mono Debugger.
- Supports Windows and macOS!

## Prerequisites ##
- [Visual Studio Code](https://code.visualstudio.com)
  - [C# Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
  - [Mono Debugger Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.mono-debug) (required for macOS debugging -- [Windows can use `clr` instead](https://github.com/OmniSharp/omnisharp-vscode/wiki/Desktop-.NET-Framework))
- [Mono](https://www.mono-project.com/docs/getting-started/install/mac/) (required for MacOS)
- [Git](https://git-scm.com)
- [7-Zip](https://www.7-zip.org) (required for Windows to decompress fnalibs)
- [Microsoft DirectX SDK (June 2010)](https://www.microsoft.com/en-us/download/details.aspx?id=6812) (required for building effects -- on Mac, [you can use Wine to run this](https://github.com/AndrewRussellNet/FNA-Template#linuxmacos-installing-the-directx-sdk-on-wine))

## Setup Instructions ##
1. Download and unzip the ZIP archive.
2. Copy+paste the resulting folder to your desired project directory.
3. Run `./getFNA.sh` (macOS) or `./win_getFNA.ps1` (Windows PowerShell) to download the latest FNA and fnalibs to the directory. (You can run this script again if you want to update either FNA or the libraries at a later point.)
4. Rename `project_name` to your project's name.
5. Open the newly-renamed project folder in Visual Studio Code.
6. Do a Find+Replace for "project_name" to the new name of your project.
7. Run the "Restore Project" build task.
8. In `.vscode/preferences.json`, change `omnisharp.autoStart` to `true`. (This will enable autocompletion and Intellisense for your project!)

That's it! Now you're ready to build and run the base project!

## Build Tasks ##
- **Restore Project:** Restores the .csproj. Run this before building for the first time, and run it again whenever you change the .csproj file.
- **Build (Debug/Release):** Builds the project with the specified configuration but does not run it. This also copies over everything in the Content/ subdirectory and the fnalibs.
- **Build and Run (Debug/Release):** Builds and runs the project. On MacOS, it runs the output with Mono. On Windows, it runs the output with .NET Framework.
- **Clean Project:** Cleans the output directories and all their subdirectories.
- **Build Effects:** Runs `fxc.exe` on all of the `.fx` files found in the Content/ subdirectories and outputs corresponding `.fxb` files that can be loaded through the Content Manager at runtime.


## Visual Studio 2022 problems with .NET 4.0
When building your project, this will try to find the .Net 4.0 SDK, but this is no longer supported from the offical VS installer. More information in this [post](https://learn.microsoft.com/en-us/dotnet/framework/install/guide-for-developers) and this [thread](https://learn.microsoft.com/en-us/answers/questions/993957/how-to-target-net-framework-4-0-in-vs-2022-on-wind)

> Starting with Visual Studio 2022, Visual Studio no longer includes .NET Framework components for .NET Framework 4.0 - 4.5.1 because these versions are no longer supported. Visual Studio 2022 and later versions can't build apps that target .NET Framework 4.0 through .NET Framework 4.5.1. To continue building these apps, you can use Visual Studio 2019 or an earlier version.

If you follow these [steps](https://stackoverflow.com/questions/78337914/how-to-target-net-framework-4-0-in-vs-2022-on-windows-11/78337958#78337958), you can start building your project without any issue 😄.

## License and Credits ##
FNA VSCode Template is released under the Microsoft Public License.
Many thanks to Andrew Russell for his [FNA Template](https://github.com/AndrewRussellNet/FNA-Template), from which I learned a lot (and borrowed a little).

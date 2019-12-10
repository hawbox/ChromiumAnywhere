# CSharp Browser for WPF

CSharp Browser is a browser development framework based on the Chromium open source project. The goal of the project is to enable .NET developers to build their own browsers using Microsoft.NET desktop technology and build hybrid web pages based on Microsoft.NET and Web. CSharp Browser has two editions, one is open-source, another is commercial, detail information please visit our GitHub (https://github.com/TangramDev) and our website (https://www.tangram.dev).

## How does WPF work?

CSharp Browser enables developers to run WPF in a browser window, fill the whole window, or share it with a web page. Unlike Silverlight, in the CSharp browser, WPF is displayed directly in the browser window without recompilation. Besides being displayed in the browser, it is no different from the standard WPF. But its advantage is that WPF can communicate with the HTML page freely, and customers can open WPF applications through URL.

To experience the CSharp Browser, you first need to make sure your computer is WIndows 7, Windows 8.1 or Windows 10, and has .NET Framework 4 or later. Download and extract the preview package to any location and run the demo MyWpfBrowser1 to MyWpfBrowser3. If everything is OK, you will see the following pictures.

[screenshots]

Customized New Tab Page using WPF.

[screenshots]

Hosted WPF applications into a browser, it was similar to Silverlight.

[screenshots]

Enable communication between WPF and webpages, developers can handle events in WPF use Javascript and vice versa.

## How to build your own browser?

You first need a computer with Windows 10 and Visual Studio 2019 installed. The following Visual Studio installation items are essential.

- .NET desktop development
- Desktop development with C++ (Required if  develop with C++)
  - Visual C++ MFC for x86 and x64
  - C++/CLI support

Also make sure you have the latest version of the Windows SDK installed.

Download tangram_runtime_chromium_78_1.0.0.zip and extract it to the `C:\src`directory.

[screenshots]

Create a WPF project (.NET Framework) using Visual Studio. And reference to `tangram_clr_rt.dll`(Located at `C:\src\tangram_runtime_chromium_78_1.0.0\`).

[screenshots]

Change platform target to x64.

[screenshots]

Update the Output path to `C:\src\tangram_runtime_chromium_78_1.0.0\`.

[screenshots]

The WPF project does not explicitly include the `Main` function by default. Developers need to delete the `App.xaml` and the `App.xaml.cs` and add a `Program` class file similar to the following:

[code snippet]

Build and run the WPF program.


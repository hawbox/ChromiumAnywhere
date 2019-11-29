# CSharp-Browser
CSharp Browser is a Chromium-based open-source browser that supports Microsoft.NET development. CSharp Browser allows developers to extend this browser using Microsoft.NET desktop technology and build hybrid web pages based on Microsoft.NET and Web.

## How to work?
CSharp Browser provides a new approach to desktop development using Chromium. You can download our preview package for experience.

Make sure your computer is Windows 7, Windows 8.1 or Windows 10, and has .NET Framework 4 or later, and Windows SDK 10.0.18362.0. Extract the downloaded preview package to any location and run the demo MyCSharpBrowser1 to MyCSharpBrowser3. The source code of demos is located in the Sources directory.

We recommend that you experience our technology with Windows 10.

![1574833869285](./assets/1574833869285.png)

The picture above is the interface of MyCSharpBrowser3.

![1574992783563](./assets/1574992783563.png)

CSharp Browser supports developers to host WinForm applications in browser tabs so that users can open WinForm applications by accessing URLs.

## How to build your own browser?
You first need a computer with Windows 10 and Visual Studio 2019 installed. The following Visual Studio installation items are essential. 

- .NET desktop development
- Desktop development with C++ (Required if develop with C++)
  - Visual C++ MFC for x86 and x64
  - C++/CLI support

Also make sure you have the correct version of the Windows SDK installed.

Create a WinForm project (.NET Framework) using Visual Studio. And reference to TangramCLR.dll.

![1574648937610](./assets/1574648937610.png)

Change platform target to x64.

![1574652601065](./assets/1574652601065.png)

Use Tangram to take over the WinForm message loop.

```c#
static void Main()
{
    Application.EnableVisualStyles();
    Application.SetCompatibleTextRenderingDefault(false);
    Application.Run(Tangram.Context); // !Important
}
```

Build project, in general, the compiled results will be output to the bin\Debug\ directory. Download chromium.zip and extract it to the bin\Debug\ directory. Run the WinForm program.

![1574749320507](./assets/1574749320507.png)

A Chromium window will open. Next, we add the following code to customize the New Tab Page.

```c#
Tangram.UpdateNewTabPageLayout(layoutXML); // New line
Application.Run(Tangram.Context);
```

UpdateNewTabPageLayout needs to pass in an XML string, similar to the following:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<ntp>
  <window>
    <node id='splitter' name='splitter' rows='1' cols='2' height='250,' width='350,100,' borderwidth='0' splitterwidth='2' middlecolor='RGB(180,180,180)'>
      <node id="clrctrl" cnnid="MyCSharpBrowser.Form1,host"></node>
      <node id="hostview"></node>
    </node>
  </window>
</ntp>
```

Build and run the WinForm program again.

![1574745234980](./assets/1574745234980.png)

The Form1 will be displayed on the left side of the browser window. Take a look at Form1.

![1574747262749](./assets/1574747262749.png)

## Troubleshoots
![1574835244140](./assets/1574835244140.png)

If your browser looks like the picture above, add an app.manifest file to your project and uncomment the following lines, and rebuild.

```xml
<compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
        <!-- A list of the Windows versions that this application has been tested on
           and is designed to work with. Uncomment the appropriate elements
           and Windows will automatically select the most compatible environment. -->

        <!-- Windows Vista -->
        <supportedOS Id="{e2011457-1546-43c5-a5fe-008deee3d3f0}" />

        <!-- Windows 7 -->
        <supportedOS Id="{35138b9a-5d96-4fbd-8e2d-a2440225f93a}" />

        <!-- Windows 8 -->
        <supportedOS Id="{4a2f28e3-53b9-4441-ba9c-d69d4a4a6e38}" />

        <!-- Windows 8.1 -->
        <supportedOS Id="{1f676c76-80e1-4239-95bb-83d0f6d0da78}" />

        <!-- Windows 10 -->
        <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />

    </application>
</compatibility>
```


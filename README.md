# EDF

2023-12-10 .NET8.0.0 Blazor https://blazor.net  WebAssembly (WASM) app to read EDF https://www.edfplus.info/ header information. Progressive web app (PWA) for offline use in any mobile, PC, Mac browser. File is analyzed locally. It is hosted on https://jussivirkkala.github.io/Blazor-EDF/ and source code in https://github.com/jussivirkkala/Blazor-EDF. 

Use Ctrl+F5 to force refresh. Install as PWA by clicking icon in the end of browser address bar.

![EDF-1](EDF-0.png)

Select EDF or BDF file e.g. from https://physionet.org/about/database/. Example https://physionet.org/content/siena-scalp-eeg/1.0.0/PN00/PN00-1.edf.  

![EDF-2](EDF-1.png)

You can copy header to clipboard or download as ascii [PN00-1.edf.txt](PN00-1.edf.txt)

# Code

There are minimal changes to default Blazor empty template. You can use .NET8 SDK https://dotnet.microsoft.com/ to build and run app: 

```
dotnet watch run
```
Code and UI is in [Pages/Home.razor](Pages/Home.razor). Additional script saveFiles.js  [wwwroot/index.html](wwwroot/index.html) for saving file. 

```
...
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, minimum-scale=1, height=device-height, viewport-fit=cover" />
<meta name="mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-capable" content="yes" />...
...
<script src="saveFile.js"></script>
<script src="_framework/blazor.webassembly.js"></script>
```
In [wwwroot/css/app.css](wwwroot/css/app.css) for mobile layout

```
html {
    overscroll-behavior: none;
    -webkit-user-select: none; /* Safari */
    -ms-user-select: none; /* IE 10 and IE 11 */
    user-select: none; /* Standard syntax */
}

body {
    overflow-y: scroll;
    overscroll-behavior: contain;
}
```

</style>


To publish app:

```
dotnet publish -c Release
```
Copy files from bin\Release\net8.0\publish\wwwroot into docs folder. You need empty .nojekyll file there and change correct folder 
```<base href="https://jussivirkkala.github.io/Blazor-EDF/" />``` in docs\index.html. Use \docs option in GitHub pages settings. 

End

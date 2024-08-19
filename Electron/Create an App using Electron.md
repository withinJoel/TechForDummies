# Create an App using Electron
## Shortcut
* Press `Ctrl + Shift + I` to open developer mode in the Electron web app.
## Get Started
* Install Node.js: Download and install Node.js from `https://nodejs.org/`.
* Create a Project Folder: Make a new folder for your app (e.g., "MyElectronApp").
* Open Command Prompt: Open a command prompt and navigate to your project folder.
* Initialize Project: `Run npm init -y` to create a package.json file.
* Install Electron: Run `npm install electron --save-dev` to install Electron.
* Create Main File: Create a file named `main.js` in your project folder.
* Add Code to `main.js`:
```
const { app, BrowserWindow, screen, Menu } = require('electron');
const path = require('path');

function createWindow() {
  const { width, height } = screen.getPrimaryDisplay().workAreaSize;   

  const emptyMenu = Menu.buildFromTemplate([]);
  const win = new BrowserWindow({
    width: 1800,
    height: 780,
    frame: true,
    autoHideMenuBar: true,
    resizable: false,
    maximizable: false,
    icon: path.join(app.getAppPath(), 'Evelina.ico'), // Replace with your icon path
    webPreferences: {
      nodeIntegration: false
    }
  });
  win.loadURL('https://evelina.pages.dev/');
  win.webContents.on('did-finish-load', () => {
    win.webContents.insertCSS(`
      html, body, #app {
        margin: 0;
        padding: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
      }
    `);
  });
  win.on('maximize', () => {
    const { width, height } = screen.getPrimaryDisplay().workAreaSize;
    win.setSize(width, height);
  });
}
app.whenReady().then(createWindow);
```
* Modify `package.json`: Replace the contents of `package.json` with:
```
{
  "name": "Elsa",
  "version": "1.1.6",
  "description": "Elsa",
  "main": "main.js",
  "scripts": {
    "start": "electron .",
    "package": "electron-packager . Elsa --platform=win32 --arch=x64 --out=dist --overwrite --icon=Elsa.ico"
  },
  "author": "Joel Jolly",
  "license": "ISC",
  "devDependencies": {
    "electron": "^31.1.0"
  }
}
```

* Test the App: Run `npm start` to test the app.
* Install required packages: `npm install -g electron-packager electron-builder`
* Run `npm run package` to create a package.
## Additional (If you want to create a setup for Windows)
* Install Inno Setup.
* Create a `run.iss` file with the following content:
```
[Setup]
AppName=Elsa
AppVersion=1.1.4
AppPublisher=Joel Jolly
AppPublisherURL=https://github.com/withinjoel/elsa
AppSupportURL=https://github.com/withinjoel/elsa/issues
AppUpdatesURL=https://github.com/withinjoel/elsa/releases
DefaultDirName={pf}\Elsa
DefaultGroupName=Elsa
OutputDir=Output
OutputBaseFilename=Setup
Compression=lzma2
SolidCompression=yes
SetupIconFile=..\Core\Logo\Elsa.ico
[Files]
Source: "Elsa\*"; DestDir: "{app}"; Flags: recursesubdirs
[Icons]
Name: "{commondesktop}\Elsa"; Filename: "{app}\Elsa.exe"; IconFilename: "{app}\Elsa.exe"
Name: "{group}\Elsa"; Filename: "{app}\Elsa.exe"; IconFilename: "{app}\Elsa.exe"
[Run]
Filename: "{app}\Elsa.exe"; Description: "{cm:LaunchProgram,Elsa}"; Flags: nowait postinstall skipifsilent
```
* Compile and run the Inno Setup script to create a setup file.
# Issues
## Icon not loading in the explorer
* Run command prompt as administrator.
* Execute the following commands:
```
ie4uinit.exe -ClearIconCache
taskkill /IM explorer.exe /F
DEL /A /Q "%localappdata%\IconCache.db"
start explorer.exe
```

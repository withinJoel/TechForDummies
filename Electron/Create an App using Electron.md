# Create an App using Electron 

## Shorcuts
`ctrl shift i` - for developer mode in the electron web app

## Get Started
1. Install Node.js
2. create a folder called as "App" or name whatever you want
3. open cmd
4. now go to the folder of you project like "cd.." and so on to the project directory and then to you created folder in this case "App"
cd your-project/App/
5. enter this command "npm init -y"
6. then this command "npm install electron --save-dev"
7. then create a main.js inside the "App" folder
8. And add these lines of code to that main.js file
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
    icon: path.join(app.getAppPath(), 'Evelina.ico'), // Use app.getAppPath() to get the resources directory
    webPreferences: {
      nodeIntegration: false
    }
  });
  

  win.loadURL('https://evelina.pages.dev/');

  // Set window margins and padding to 0
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

  // Listen for maximize event to adjust the window size
  win.on('maximize', () => {
    const { width, height } = screen.getPrimaryDisplay().workAreaSize;
    win.setSize(width, height);
  });
}

app.whenReady().then(createWindow);
```
9. Then remove all the contents from the package.json and add this code 
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
10. Once all the testing is over, It's now time to extract the app (`npm start` to test the program)
11. enter this command in the cmd in the same location where the main.js is present.
npm install -g electron-packager electron-builder
12. Then type "npm run package" in the cmd.
13. to create a package install inno setup from this site.
14. And create a run.iss file outside the folder that you want to compress and make a setup.
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
15. open the code using iss and compile and run 
16. done!

/////////////////////////////////////////////////////////////////Issues/////////////////////////////////////////////////////////////////////////////////////////////
## Icon not loading in the explorer
* run cmd as admin
* paste this code 
```
ie4uinit.exe -ClearIconCache
taskkill /IM explorer.exe /F
DEL /A /Q "%localappdata%\IconCache.db"
start explorer.exe
```
#   UTILIZANDO ELECTRON

<br>

<p>Esses dias pensei em colocar o web site Quora como um sofware para o meu computador, então pensei em utilizar a lindeza do Electron.
então vamos para a captura de web sites para sofwares</p>

<br>

```js
mkdir my-electron-app && cd my-electron-app
npm init
```

### (você deve ter o node instalado em seu computador)

<br>
<p>Entre nesse arquivo .json</p>

![image](https://github.com/pedrosalomaodw/utilizando-electron/assets/74951282/6d8dc32a-fb3a-4480-9af5-8bd22a688b49)

<br>

<p>Em seguida escreva exatamente assim:</p>

![image](https://github.com/pedrosalomaodw/utilizando-electron/assets/74951282/a1695074-da6b-4a43-89f3-c8fc45db701c)
<br>

<p>Ao fazer isso, crie um arquivo js e coloque o seguinte código:</p>

```js
const { app, BrowserWindow } = require('electron/main')
const fs = require('node:fs')
const path = require('node:path')

function createWindow () {
  const win = new BrowserWindow({
    width: 1920,
    height: 1080
  })

  win.loadURL('link do site que você quer')
}

const fileName = 'recently-used.md'
fs.writeFile(fileName, 'Lorem Ipsum', () => {
  app.addRecentDocument(path.join(__dirname, fileName))
})

app.whenReady().then(createWindow)

app.on('window-all-closed', () => {
  app.clearRecentDocuments()
  if (process.platform !== 'darwin') {
    app.quit()
  }
})

app.on('activate', () => {
  if (BrowserWindow.getAllWindows().length === 0) {
    createWindow()
  }
})
```
<br>
<p>(Caso você queira colocar seu web site para sofware, recomendo que mude o loadURL para loadFile e adicione "index.html" para carregar tudo corretamente)</p>
<p>Agora coloque no terminal: npm install e em seguida escreva "npm run start" para rodar o programa e pronto! seu programa em electron está rodando perfeitmente bem.</p>
<br>

![image](https://github.com/pedrosalomaodw/utilizando-electron/assets/74951282/4dedeac2-ce1f-4ee3-8b41-97e86feec2d4)



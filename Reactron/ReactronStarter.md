# Reactron(React + Electron) Starter

## 깃허브 프로젝트 리스트

- <https://github.com/alanbsmith/react-electron-starter> (이건 진짜 스타터 webpack, babel등 사용)

- <https://github.com/christiannwamba/scotch-player> (이건 음악플레이어를 React와 Electron을 사용하여 구현한것)(<https://scotch.io/tutorials/build-a-music-player-with-react-electron-i-setup-basic-concepts> 해당 블로그 참조)

windows기준임을 알립니다.

## 직접 작업환경 설정하기 (작업환경임에 유의)

1. create-react-app (React폴더의 React-create.md참조)
2. npm install --save-dev electron
3. Electron entry js 파일을 src 폴더에 추가 (main.js를 Electron-Quick-Start 프로젝트에서 복사한뒤, electron-starter.js로 리네임)(Electron폴더의 Electron-Quick-Star.md 문거 참조)
4. set `mainWindow.loadURL` to `'http://localhost:3000'`
5. `"main": "src/electron-starter.js"` 을 package.json에 추가한다. (main entry이다.)
6. `"electron": "electron ."` 스크립트를 package.json에 추가한다.
7. npm start를 한뒤, npm run dev를 한다. (cmd를 2개 실행한다)

## 배포하기
1. ```npm run build``` react를 배포파일로 빌드한다.
2. electron-packager를 사용해 electron 실행파일로 배포한다. (Electron폴더의 Electron-packager.md 문서 참조)

## 더 편하게 개발하기 (optional, React와 Electron을 동시에 실행하기)

1. `"electron-dev": "set ELECTRON_START_URL=http://localhost:3000 && electron .""`를 package.json에 추가
2. `mainWindow.loadURL`를 다음과 같이 수정
```
const startUrl = process.env.ELECTRON_START_URL || url.format({
            pathname: path.join(__dirname, '/../build/index.html'),
            protocol: 'file:',
            slashes: true
        });
    mainWindow.loadURL(startUrl);
```
3. ```"homepage": "./",```를 package.json에 추가
4. npm install --save-dev foreman
5. 루트에 Procfile파일 추가 내용은 아래와 같음
```
react: npm start
electron: npm run electron
```
6. src에 electron-wait-react.js파일을 추가 내용은 아래와 같음
```
const net = require('net');
const port = process.env.PORT ? (process.env.PORT - 100) : 3000;
process.env.ELECTRON_START_URL = `http://localhost:${port}`;
const client = new net.Socket();
let startedElectron = false;
const tryConnection = () => client.connect({port: port}, () => {
        client.end();
        if(!startedElectron) {
            console.log('starting electron');
            startedElectron = true;
            const exec = require('child_process').exec;
            exec('npm run electron');
        }
    }
);
tryConnection();
client.on('error', (error) => {
    setTimeout(tryConnection, 1000);
});
```

https://github.com/facebookincubator/create-react-app
https://medium.freecodecamp.com/building-an-electron-application-with-create-react-app-97945861647c

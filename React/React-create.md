# React-create
간편하게 react와 react-dom은 물론, 개발에 필요한 webpack과 babel들까지 한번에 설치할 수 있는 방법이다.
https://velopert.com/2037

```
// 한번 글로벌 -g로 설치해 두면, 다른 곳에서는 create명령만으로도 사용할 수 있다.
npm install -g create-react-app

create-react-app hello-world
```

package.json을 확인해 보면, devDependency에 react-scripts만 있는걸 확인 할 수 있는데, 이는 webpack들이 react-scripts에 들어있다.
이것을 해체 할 수도 있다.
```
npm run eject
```
을 하면, package.json이 아래와같이 바뀐다.

```
{
  "name": "hello-world",
  "version": "0.0.1",
  "private": true,
  "devDependencies": {
    "autoprefixer": "6.3.7",
    "babel-core": "6.10.4",
    "babel-eslint": "6.1.2",
    "babel-loader": "6.2.4",
    "babel-plugin-syntax-trailing-function-commas": "6.8.0",
    "babel-plugin-transform-class-properties": "6.10.2",
    "babel-plugin-transform-object-rest-spread": "6.8.0",
    "babel-plugin-transform-react-constant-elements": "6.9.1",
    "babel-preset-es2015": "6.9.0",
    "babel-preset-es2016": "6.11.3",
    "babel-preset-react": "6.11.1",
    "chalk": "1.1.3",
    "cross-spawn": "4.0.0",
    "css-loader": "0.23.1",
    "eslint": "3.1.1",
    "eslint-loader": "1.4.1",
    "eslint-plugin-import": "1.10.3",
    "eslint-plugin-react": "5.2.2",
    "extract-text-webpack-plugin": "1.0.1",
    "file-loader": "0.9.0",
    "fs-extra": "^0.30.0",
    "html-webpack-plugin": "2.22.0",
    "json-loader": "0.5.4",
    "opn": "4.0.2",
    "postcss-loader": "0.9.1",
    "rimraf": "2.5.3",
    "style-loader": "0.13.1",
    "url-loader": "0.5.7",
    "webpack": "1.13.1",
    "webpack-dev-server": "1.14.1"
  },
  "dependencies": {
    "react": "^15.2.1",
    "react-dom": "^15.2.1"
  },
  "scripts": {
    "start": "node ./scripts/start.js",
    "build": "node ./scripts/build.js"
  }
}
```

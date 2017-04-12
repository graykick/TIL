# publishing
React로 Marquee 컴포넌트를 만들었다.
이를 github뿐만 아니라, NPM에 배포해서 다른 사람들도 사용할 수 있도록 하려는데 목적을 두었다.
단순 배포하는 것이 아닌, 실제 여러 라이브러리들을 사용하는것 과 같이 install을 통하여 import후 사용할 수 있도록 하려고 한다.

## 배포준비
1. npm init
2. publishing할 모듈(컴포넌트)에 필요한 dependency들 install 하기 (나의 경우는 react, react-dom을 추가하였음)
3. 모듈(컴포넌트)를 루트폴더에 추가 (나의경우 MarqueeDouble.js를 추가하였음)
4. npm install babel-cli babel-preset-es2015 babel-preset-react  babel-preset-stage-0 --save-dev 개발에 필요한 dependency install
5. package.json에 babel preset 설정 아래의 코드 추가
```
"babel": {
    "presets": [ "es2015", "react"]
  }
```
6. babel을 사용하여 js 변환.
```
babel MarqueeDouble.js -o index.js
```
7. publishing script를 package.json에 추가
```
"scripts": {
   "build": "./node_modules/.bin/babel MarqueeDouble.js -o index.js",
   "prepublish": "npm run build"
 }
```

여기까지 배포 전 단계까지 완료하였다.

## github에 올려 테스트해보기
1. github에 add, commit, push
2. github에 push한 component install
```
npm install git+https://git@github.com/[your git username]/[your git repo name].git --save
// 나의 경우 git+https://git@github.com/graykick/react-marquee-double.git
```
3. import하여 사용해보기
```
import yourComponent from 'your-component-name';

...

<yourComponent>
```

## NPM에 올리기
1. 터미널에서 npm publish

끝!
이제 npm에 나의 component가 업로드 되었다.

컴포넌트를 수정했을때는, **package.json의 version을 올린후** 다시 ```npm publish```를 하면 된다.


참고링크
http://frontendinsights.com/how-create-react-component-publish-npm/
http://rajasekarm.com/pushing-react-component-into-npm

# NODE - SCSS 사용방법
SCSS 기본에 대해 알아 봅시다.

#### Getting-Started
0. 프로젝트 폴더를 원하는 위치에 생성한다.
```
/*터미널*/
mkdir 프로젝트명
ex) mkdir A-project
```

1.프로젝트 폴더에 터미널로 들어가서 명령어 실행
  ```
  /*터미널*/
  npm install -g node-sass     //NPM node(팩키지들을)(글로벌에 설치하겠다.)
  npm install node-sass     //NPM node(팩키지들을)(로컬에 설치하겠다.)
  ```
내 프로젝트 폴더 안에  
로컬로 node_modules이라는 폴더가 생성되어야만 한다.


```
/*터미널*/
npm install scss-compile scss-compile -g  //scss처음 사용할때만 작성하는 명령어(글로벌에 설치하겠다.)
```
2. package.json 파일 만들기
  ```
  /*터미널*/
  npm init      //여러 옵션을 설정할때 사용한다. (선택 사항)
  npm init -y   //여러 옵션을 기본값으로 사용할때 쓴다. (선택 사항)
  ```
  ```
  /*package.json*/
  {
    "name": "module-sass",
    "version": "1.0.0",
    "description": "",
    "main": "index.js”,
    /*------------------------추가------------------------------
      "scripts": {
      "test": "npm run scss-compile",
      "scss-compile": "node-sass -rw SASS/main.scss -o style/css",
      "watch": "npm run scss-compile"
    },
    */---------------------------------------------------------
    "author": "",
    "license": "ISC",
    "dependencies": {
    "node-sass": "^4.10.0"
    }
  }
  ```


3. index.js 및 index.html을 생성해 작성하십시오

  ```html
  <!-- index.html -->
  <html>
    <head>
      <title>webpack 2 demo</title>
    </head>
    <body>
      <script src="app/index.js"></script>
    </body>
  </html>
  ```
  ```js
  // index.js
  function component () {
    var element = document.createElement('div');

    element.innerHTML = _.join(['Hello','webpack'], ' ');

    return element;
  }
  
  document.body.appendChild(component());
  ```
  
  4. 이 명령을 사용하여 node_modules파일을 생성한다.
  ```
  npm install webpack --save-dev 
  ```
  ![alt text](http://younhoso.co.kr/webpackImg/webpack1.png)<br/>
  사진과 같이
  <strong>node_modules</strong> 파일이 생성된것을 확인 할수 있다.


  5. 이 명령을 사용하여 lodash 라이브러리를 설치하십시오.

  ```
  /*터미널*/
  npm i lodash --save
  ```
  그리고 import 코드를 추가시켜준다.
  ```js
  // index.js
  import _ from 'lodash'; //(추가시켜준다.)
  
  function component () {
    var element = document.createElement('div');

    element.innerHTML = _.join(['Hello','webpack'], ' ');

    return element;
  } 
  
  document.body.appendChild(component());
  ```
  6.webpack.config.js파일을 생성하고, 아래 코드를 추가 시켜준다.
  ```js
  //webpack.config.js
  var path = require('path');

  module.exports = {
    entry: './app/index.js',  // 번들링할 대상을 말한다.
    output: {                 // 번들링을 했을때 나오는 결과물
      filename: 'main.js',
      path: path.resolve(__dirname, 'dist')   //__dirname라고한것을 절대경로를 현재 폴더까지 생략해서 __dirname라고만 칭하는 것이다. 
    }
  };
  ```
  7. webpack 빌드
  장점: webpack.config.js를 구성하고, webpack라고만 명령어 치면 자동으로 webpack.config.js파일을 찾는다. 그리고 그안에 로직대로 빌드를 실행한다.
  ```
  /*터미널*/
  webpack
  ```
  
  
# Webpack scss build 사용방법

#### Getting-Started

초반 세팅은 위에서 3번 내용까지 동일합니다.

4. 이 명령을 사용하여 webpack에서 sass build 하기위해 필요한 모든 라이브러리를 철시한다.
  
  ```
  /*터미널*/
  npm i sass-loader node-sass webpack style-loader css-loader --save-dev
  ```
  
  5. webpack.config.js파일을 생성하고, 아래 코드를 추가 시켜준다.
  ```js
  //webpack.config.js
  var path = require('path');

  module.exports = {
    entry: './app/index.js',  // 번들링할 대상을 말한다.
    output: {                 // 번들링을 했을때 나오는 결과물
      filename: 'main.js',
      path: path.resolve(__dirname, 'dist')   //__dirname라고한것을 절대경로를 현재 폴더까지 생략해서 __dirname라고만 칭하는 것이다. 
    }
  },
  ---------------------------- //다음내용 추가
    module: {
      rules: [
          {
            test: /\.scss$/,
            use: [
              'style-loader',
              'css-loader',
              'sass-loader'
            ]
          }
      ]
    },
  ----------------------------
  };
  ```
  6. 번들링할 대상 파일에서(index.js) scss파일도 불러온다.
 ```js
  // index.js
  import '../styles/scss/style.scss';//(추가시켜준다.)
  import _ from 'lodash'; 
  
  function component () {
    var element = document.createElement('div');

    element.innerHTML = _.join(['Hello','webpack'], ' ');

    return element;
  } 
  
  document.body.appendChild(component());
  ```
  7. webpack 빌드
  장점: webpack.config.js를 구성하고, webpack라고만 명령어 치면 자동으로 webpack.config.js파일을 찾는다. 그리고 그안에 로직대로 빌드를 실행한다.
  ```
  /*터미널*/
  webpack
  ```
  
  ![alt text](http://younhoso.co.kr/webpackImg/webpack2.png)<br/> 
  다음과 같은 순서대로 빌드된다.
  

# NODE - SCSS 사용방법
SCSS 실시간으로 자동으로 compile에 대해 알아 봅시다.

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

![alt text](http://younhoso.synology.me/web_images/webtest2.png)<br/> 

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
      "scss-compile": "node-sass -rw SCSS/main.scss -o style/",  //scss파일은 감지하고 있다가. 변경이 되면 자동으로 지정한 위치에 compile하겠다는 명령어
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
https://www.npmjs.com/package/scss-compile 
공식사이트 참고

```
/*터미널*/
npm run scss-compile     //scss-compile 실행하겠다.
```

![alt text](http://younhoso.co.kr/webtestImg/webtest1.png)<br/> 
scss파일 css로 컴파일 되는 모습  

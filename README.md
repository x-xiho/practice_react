#react 연습 < 나 혼자 보는 메모장 >
---
- [ ] power BI 사용법 익히기
- [ ] 데이터 시각화 자료 레퍼런스 모으기 -> 지도 위주면 좋고
- [ ] azure 사용방법 익히기 -> 녹화강의 복습
- [ ] 리액트 훅 익히기
- [ ] 백엔드 이해
      

### VSC에 React 세팅하는 방법
* node.js 설치
* 프로젝트 파일 생성
* vsc에서 프로젝트 파일 오픈 후 터미널에 아래 문장 입력하여 세팅하기

```npx create-react-app <프로젝트 명>```  

### react 화면 띄우기 

```
cd <프로젝트명>
npm start
```

* 꼭 cd 프로젝트명 먼저 입력 후 미리보기 시작할 것!


### react에 powerBI 넣는법
1. package.json에 아래와 같이 입력. 마지막 숫자는 최신버전으로 입력  

```
powerbi-client-react": "^1.4.0" 
```

2. App.js에 다음과 같이 입력
```
import { PowerBIEmbed } from 'powerbi-client-react';
```


### 리액트 페이지 연결하기 ( react-router-dom)

*[리액트 라우팅 참고영상](https://www.youtube.com/watch?v=xVeFY1Eq28g)  

**1. 리액트 라우터 돔 모듈 설치하기**
```
npm i react-router-dom
```

**2. react-router-dom import하기**
```
import {BrowserRouter, Routes, Route } from 'react-router-dom'
```

**3. 라우팅 포맷**
```
<BrowserRouter>
<Routes>
<Route path="/" element={<App/>}/>
</Routes>
</BrowserRouter>
```



### 부트스트랩 설치
```
npm install react-bootstrap bootstrap

import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/css/bootstrap.min.css';
```


---
**현재 문제점**
* 내가 프로젝트를 잘 완수할 수 있을까. 프론트엔드 기본 지식을 언넝 공부해서 따라가야할 것 같다...
* vsc 파일 작성하고 깃허브에 연동하려고 하면 에러가 뜬다. 경로가 꼬인거 같은데 뭐가 문제인지 모르겠다. 깃허브 사용 방법을 더 자세히 찾아봐야할듯
* 리액트 세팅 시 왜 빨간색 에러가 나오는지 모르겠다. 지금 또 입력하니 문제 없이 작동하는데.. 일단 더 지켜보고 또 에러가 나면 해결해야겠다.
* 데이터 문제 -> 시/구까지는 괜찮은데 동으로 가면 지도의 정확성이 많이 떨어진다. 구를 사용할 때도 조금의 에러가 있는듯. 웬만하면 정확한 주소/ 위도 경도가 있는 데이터를 사용해야할듯 하다. 
  


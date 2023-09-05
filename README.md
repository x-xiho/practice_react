#react 연습 < 나 혼자 보는 메모장 >
---
- [ ] power BI 사용법 익히기
- [ ] 데이터 시각화 자료 레퍼런스 모으기 -> 지도 위주면 좋고
- [ ] azure 사용방법 익히기 -> 녹화강의 복습
- [ ] 리액트 훅 익히기
- [ ] 백엔드 이해
- [ ] axios 공부
      

### VSC에 React 세팅하는 방법
* node.js 설치
* 프로젝트 파일 생성
* vsc에서 프로젝트 파일 오픈 후 터미널에 아래 문장 입력하여 세팅하기

```npx create-react-app <프로젝트 명>```  
* axios 설치  
```npm i -save axios```  
```import axios from```   

### react 화면 띄우기 

```
cd <프로젝트명>
npm start
```

* 꼭 cd 프로젝트명 먼저 입력 후 미리보기 시작할 것!

-------------------------------
### react에 powerBI 넣는법
*[리액트 파워비아이 임베딩 참고영상](https://blog.naver.com/jimin201396/223160116243)
1. package.json에 아래와 같이 입력. 마지막 숫자는 최신버전으로 입력  

```
powerbi-client-react": "^1.4.0" 
```

2. App.js에 다음과 같이 입력
```
import { PowerBIEmbed } from 'powerbi-client-react';
```

-----------------------
### 리액트 페이지 연결하기 ( react-router-dom)

*[리액트 라우팅 참고영상](https://www.youtube.com/watch?v=xVeFY1Eq28g)  

**1. 리액트 라우터 돔 모듈 설치하기**
```
npm i react-router-dom
```

정상적으로 설치가 완료되면 json 파일에
"react-router-dom": "^6.15.0", 가 추가된다. 

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

**4. 중첩 라우팅**
```
<Route element={<Navbar/>}/>
      <Route path="" element={<App/>}/>
</Route>
```
특정 컴포넌트를 고정시키고 새로운 컴포넌트를 띄우고 싶을때 사용함

---------------------------------
### 부트스트랩 설치
```
npm install react-bootstrap bootstrap

import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/css/bootstrap.min.css';
```


--------------------------

### 리액트 개념 설명
*[참고 사이트](https://webstoryboy.co.kr/1934)

---
**현재 문제점**
* 데이터 문제 -> 시/구까지는 괜찮은데 동으로 가면 지도의 정확성이 많이 떨어진다. 구를 사용할 때도 조금의 에러가 있는듯. 웬만하면 정확한 주소/ 위도 경도가 있는 데이터를 사용해야할듯 하다.
* 구체적인 페이지 디자인이 필요하다
* 로그인 구현 어떻게 하는거지
* 에이징 테크 컨셉을 잘 보여주려면 어떤 UI/UX를 만들어야하는지
  


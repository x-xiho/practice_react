#react 연습 < 나 혼자 보는 메모장 >
---
- [ ] power BI 사용법 익히기
- [ ] 데이터 시각화 자료 레퍼런스 모으기 -> 지도 위주면 좋고
- [ ] azure 사용방법 익히기 -> 녹화강의 복습
- [ ] 리액트 훅 익히기
- [ ] 백엔드 이해
- [ ] axios 공부
      
*[리액트 무료 강의 (환경세팅에서 배포까지)](https://www.youtube.com/watch?v=WS6mlo2C-M8&list=PLK7AWkPYwus6emABbBT0hYDTBO2w1tyzn)

### VSC에 React 세팅하는 방법
* node.js 설치
* 프로젝트 파일 생성
* vsc에서 프로젝트 파일 오픈 후 터미널에 아래 문장 입력하여 세팅하기

```npx create-react-app <프로젝트 명>```  

rfce 입력하면 포맷 제공

### AXIOS 사용방법
*[axios 공식문서](https://axios-http.com/kr/docs/intro)  
```npm install axios --save```  
```import axios from 'axios' ```

```
axios.get("https://raw.githubusercontent.com/yopy0817/data_example/master/hi.json")
.then(response => consol.log(response.data))
```
axios의 반환은 promise ( fetch와 동일 )
단 데이터를 전달할 때 한 번에 data: ~~~ 로 주기 때문에 json 변형 과정을 안 거쳐도 됨.

* async await 문법
*[관련 티스토리](https://coding404.tistory.com/21)
async = 이거 비동기임  
await = 비동기니까 기다려

function 앞에 async를 추가하면 항상 프로미스를 반환한다. 
리턴이 프로미스면 await를 적용하고 then절을 없앨 수 있다. 
어싱크, 어웨잇은 동기적바익(순서) 보장한다.
##### 장점 : 코드가 간결해짐/동기적인 방식을 보장해줌

```
const handleClick = async () => {
      let response = await axios.get("https://raw.githubusercontent.com/yopy0817/data_example/master/hi.json")
      console.log(response.data);
      setData(response.data);

      consol.log(1)

      let response2 = await axios.get("https://raw.githubusercontent.com/yopy0817/data_example/master/hello.json")
      console.log(response2.data)
      setData(response2.data)

      consol.log(2)
}
```


##### 변경 전  
```
axios.get("")
.then (data => setData(data))
```

##### 변경 후 
```
const handleClick2 = async () => { // 이거 비동기 함수야~
      const result = await axios.get("") // then절 없이 프로미스 리턴 받을 수 있어~ 
}
```
   

### react 화면 띄우기 

```
cd <프로젝트명>
npm start
```

* 꼭 cd 프로젝트명 먼저 입력 후 미리보기 시작할 것!


-------------------------------
### REACT Hook 
```
const [data, setData ] = useState()

useEffect = () => {
// 함수
, [] }

const dataRef = useRef()

 
```

-------------------------------
### react에 powerBI 넣는법
*[리액트 파워비아이 임베딩 참고](https://blog.naver.com/jimin201396/223160116243)
1. package.json에 아래와 같이 입력. 마지막 숫자는 최신버전으로 입력하고 npm install
*[pwerbi-client-react 최신 버전 확인](https://www.npmjs.com/package/powerbi-client-react?activeTab=readme)

```
"powerbi-client-react": "^1.4.0" 
```

2. 임베딩할 컴포넌트에 powerbi import
```
import { PowerBIEmbed } from 'powerbi-client-react';
import { models } from 'powerbi-client'
```

3. embed code 임력
```
<PowerBIEmbed
	embedConfig = {{
		type: 'report',   // Supported types: report, dashboard, tile, visual, qna, paginated report and create
		id: '<Report Id>',
		embedUrl: '<Embed Url>',
		accessToken: '<Access Token>',
		tokenType: models.TokenType.Aad, // Use models.TokenType.Aad for SaaS embed
		settings: {
			panes: {
				filters: {
					expanded: false,
					visible: false
				}
			},
			background: models.BackgroundType.Transparent,
		}
	}}

	eventHandlers = {
		new Map([
			['loaded', function () {console.log('Report loaded');}],
			['rendered', function () {console.log('Report rendered');}],
			['error', function (event) {console.log(event.detail);}],
			['visualClicked', () => console.log('visual clicked')],
			['pageChanged', (event) => console.log(event)],
		])
	}

	cssClassName = { "embededReport" }

	getEmbeddedComponent = { (embeddedReport) => {
		window.report = embeddedReport;
	}}
/>
```

4. 마이크로소프트 사이트에서 try it 버튼을 눌러 각종 소스를 받아온다.
*[Get Report](https://learn.microsoft.com/en-us/rest/api/power-bi/reports/get-report)
* reportID는 powerbi 홈페이지 주소창에서 긁어오기
* accessToken은 powerbi 작업물 개발자도구에서 copy(accessToken) 입력하여 복사붙여넣기


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

### 리액트 포트폴리오 작성해보기 
*[참고 사이트](https://webstoryboy.co.kr/1934)

### 리액트에서 로컬스토리지를 사용하여 로그인 구현하기
*[리액트에서 로컬스토리지로 로그인 구현하기](https://velog.io/@choco1drink/React-LocalStorage-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84)

### 카카오 소셜 로그인
*[카카오 로그인](https://stack94.tistory.com/entry/React-%EC%B9%B4%EC%B9%B4%EC%98%A4Kakao-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84%ED%95%B4%EB%B3%B4%EA%B8%B0)

---
**이게 뭐야**
* 소셜 로그인시 왜 kakao 어쩌구가 key로 들어오는거지
*[횡스크롤 css](https://github.dev/blueWeber/css-horizontal-scroll-contents)
---
**현재 문제점**
* 데이터 문제 -> 시/구까지는 괜찮은데 동으로 가면 지도의 정확성이 많이 떨어진다. 구를 사용할 때도 조금의 에러가 있는듯. 웬만하면 정확한 주소/ 위도 경도가 있는 데이터를 사용해야할듯 하다.
* 구체적인 페이지 디자인이 필요하다
* 로그인 구현 어떻게 하는거지
* 에이징 테크 컨셉을 잘 보여주려면 어떤 UI/UX를 만들어야하는지
* 토큰 만료 문제!!! -> 파워비아이 유료 버전 사용밖에 답이 없는지?? 어떻게 자동으로 토큰 연장을 하는지 찾아봐야 한다

*[자동 연장 방법](https://learn.microsoft.com/en-us/javascript/api/overview/powerbi/refresh-token)
*[정상적인 임베딩 방법](https://learn.microsoft.com/en-us/power-bi/developer/embedded/register-app?tabs=customers)

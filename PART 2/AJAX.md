# Q. AJAX에 대해 설명해주세요.

## 1. 질문의 의도


## 2. 개념 설명

### AJAX란 
- Asynchronous Javascript And XML(비동기식 자바스크립트와 XML)의 약자
- 빠르게 동작하는 동적인 웹 페이지를 만들기 위한 개발 기법의 하나
- 브라우저가 가지고있는 XMLHttpRequest 객체를 이용해서 웹 페이지 전체를 다시 로딩하지 않고도, 웹 페이지의 일부분만을 갱신한다.
- JavaScript를 사용한 비동기 통신, 클라이언트와 서버간에 XML 데이터를 주고받는 기술
- XML이라고 명시되어있지만 다른 데이터 객체들도 사용가능해져, 서버와 JSON, XML, HTML, 텍스트 파일 등 다양한 형태의 데이터를 주고 받을 수 있다. (대부분 JSON)

### AJAX를 쓰는 이유 및 장점
- AJAX가 등장하기 이전에는 웹 브라우저(클라이언트)는 서버로부터 받은 마크업 데이터(HTML)를 브라우저 창에 렌더링하는 일을 했다. (Server Side Rendering 방식으로 렌더링된다.)
- 일부만 변경하고자 하는 경우에도, 웹 브라우저는 매번 똑같은 페이지를 처음부터 다시 렌더링해야 했고 서버 역시 매번 같은 페이지를 렌더링(이 경우에는 HTML 파일 생성)해야 해서 서로 부담이 되었다.)
- AJAX를 통해 클라이언트는 필요한 데이터만 서버를 통해 비동기적으로 받고, 페이지의 일부만 동적으로 업데이트 할 수 있다. (Client Side Rendering 방식으로 렌더링된다.)
- 예전에는 XMLHttpRequest API를 이용하는 것이 일반적이었으며, 그리고 불편함을 느낀 사람들이 jQuery를 통해 AJAX를 구현하기 시작했다.
- 요즘은 ES2015 표준으로 Fetch API가 등장하면서부터 비동기(Promise) 방식의 Fetch API를 주로 이용해서 AJAX를 구현한다.

### AJAX의 한계 및 단점

## 3. 답변

🔗 참고 자료
- https://99geo.tistory.com/65
- https://hanamon.kr/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-ajax%EB%9E%80-spa%EB%A5%BC-%EB%A7%8C%EB%93%9C%EB%8A%94-%EA%B8%B0%EC%88%A0/

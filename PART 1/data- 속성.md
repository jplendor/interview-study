# Q. data-* 속성에 대해 설명해주세요.

## 1. 질문의 의도
data-* 속성이 왜 등장했는지, 단점 및 권장되지 않는 이유를 알고 있는가?

## 2. 개념 설명

### data-* 속성이란?
- HTML5에서 새롭게 등장한 속성이다.
- 목적: 데이터를 HTML에(DOM 요소에) 저장하기 위해
- (과거에는 HTML에 데이터를 저장하기 위해 input[type='hidden']을 쓴다든가 하는 꼼수를 쓰곤 했다.)
   - ```
     <input type="hidden" value="2"><button class="del-btn">삭제</button>
     ``` 
- 어느 엘리멘트에나 data-로 시작하는 속성으로 작성하면 된다. ex data-job, data-color, data-age
- 사용자 지정 데이터 속성이다. (= 개발자가 정의하고 싶은 대로 정의해서 사용한다.)


### 문법/사용법

HTML

  ```
    <div id="user1" data-full-name="jessica alba kim" data-gender="female">jessica</div>
    <div id="user2" data-full-name="john park" data-gender="male">john</div>
  ```
  
JavaScript
  
  ```
    const user1 = document.getElementById("user1")
    console.log(user1.dataset.fullName)
    console.log(user1.dataset.gender)
  ```
  
CSS
  
  ```
    div[data-gender="male"] {
      background-color: yellow;
    }  
  ```
<kbd>
  <img src="https://user-images.githubusercontent.com/97583339/179926329-08940d08-32a7-41cc-91ad-ccc8298a5d5c.png" />
</kbd>
  
### 장점
- 화면에 보이지도 않고, 레이아웃에도 영향을 주지 않으면서 HTML 요소에 쉽게 여러 데이터를 저장할 수 있다.
- 즉, hidden으로 태그를 숨여두고 데이터를 저장할 필요가 없기 때문에 HTML 코드가 더 깔끔해진다.
- CSS, JavaScript에서도 쉽게 접근하여 읽거나 쓸 수 있다.
  
### 단점 및 유의할 점
- HTML에 데이터를 넣는 것이기 때문에 누구에게나 보이고, JavaScript로 접근 가능하기 때문에 누구나 수정할 수 있다. 
- 즉, 민감한 정보는 저장하지 않는 것이 좋다.
- 검색엔진에 노출되어야할 내용은 data-* 속성에 넣지 않는다.
- JavaScript 데이터 저장소에 저장하는 것과 비교해서 데이터 속성 읽기의 성능이 저조하다.

## 3. 답변

data-* 속성은 HTML5에서 HTML 요소에 데이터를 저장하기 위한 목적으로 등장한 속성입니다. 
HTML 요소에 데이터를 저장하기 때문에 안전하지 않고, JavaScript 데이터 저장소에 저장하는 것과 비교해서 데이터 속성 읽기의 성능이 저조합니다.
요즘은 JavaScript 라이브러리나 프레임워크의 데이터 바인딩을 통해 DOM을 업데이트된 상태로 유지하는 방법이 더 쓰이고 있습니다.

🔗 참고 자료

- https://developer.mozilla.org/ko/docs/Learn/HTML/Howto/Use_data_attributes
- https://www.zerocho.com/category/HTML&DOM/post/5a76d1eaabd090001b981ba6
- https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-HTML-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%85%8Bdata-%EC%86%8D%EC%84%B1
- https://www.frontendinterviewhandbook.com/kr/html-questions#data-%EC%86%8D%EC%84%B1%EC%9D%80-%EB%AC%B4%EC%97%87%EC%97%90-%EC%A2%8B%EC%9D%80%EA%B0%80%EC%9A%94

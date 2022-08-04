# Q. Virture DOM(가상 돔)에 대해 설명해주세요.

## 1. 질문의 의도
리액트의 주요 특징인 가상 돔에 대해 알고있는가?

## 2. 개념 설명

### DOM 
- Document Object Model (문서 객체 모델)
- XML이나 HTML 문서에 접근하기 위한 일종의 인터페이스
- 문서의 구조화된 표현(structured representation)을 제공하며 (트리 구조로 표현)
- 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공하여, (API - ex. querySelector())
- 문서 구조, 스타일, 내용 등을 변경할 수 있게 돕는다.
- nodes와 objects로 문서를 표현 (웹 페이지를 스크립트 또는 프로그래밍 언어들에서 사용될 수 있게 연결시켜주는 역할)
![image](https://user-images.githubusercontent.com/97583339/182066584-3cf1b208-d9c3-4c7d-88fe-46cdfecf42d3.png)

### DOM 조작 과정
- HTML을 탐색하여 해당 엘리먼트를 찾는다.
- 해당 엘리먼트와 자녀 엘리먼트를 DOM에서 제거한다.
- 새로운 엘리먼트로 교체한다.
- CSS 계산, 레이아웃 과정(reflow), 화면에 그리기(repaint)를 수행한다.
- (이때, reflow, repaint 과정에서 많은 리소스가 소모되는데, 가상 돔을 사용하여 Batch Update 하면, 이 과정을 한번으로 줄일 수 있다.)

### Virture DOM(가상 돔)
- 실제 돔의 복사본
- 자바스크립트 객체 형태로 메모리상에 저장되어있다.

### Virture DOM(가상 돔)을 이용한 DOM 조작 과정

- 리액트는 두 개의 가상 돔을 가지고 있음
  - 렌더링 이전 화면 구조를 나타내는 가상 돔
  - 렌더링 이후에 보이게될 화면 구조를 나타내는 가상 돔
- 변경된 내용이 화면에 새롭게 그려지기 전에(실제 돔이 변경되기 이전에), 두 개를 비교하여 바뀐 부분을 찾아냄 (diffing)
- 바뀐 부분만 실제 돔에 적용시킨다.
- 변경된 모든 엘리먼트를 한꺼번에 집단으로 적용시킨다. (Batch Update)
- 이러한 과정을 reconciliation(재조정)이라고 한다.

## 3. 답변
가상 돔은 실제 돔 조작 과정에서 필요한 비효율적인 리소스 소모를 효율적으로 줄이기 위해 나온 개념입니다.  
리액트에서의 가상 돔 조작 과정은 다음과 같습니다.  
변경 전, 후에 해당하는 두 개의 가상 돔이 있고, 이를 diffing 알고리즘을 통해 바뀐 부분을 찾아내고, 바뀐 부분을 한번에 적용시킵니다.  
이러한 재조정 과정을 통해 리액트는 동적인 웹 페이지를 빠르고 효율적으로 처리할 수 있습니다.

🔗 참고 자료
- https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction
- https://www.youtube.com/watch?v=gc-kXt0tjTM
- https://junilhwang.github.io/TIL/Javascript/Design/Vanilla-JS-Virtual-DOM/#_3-%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%A1%E1%84%8B%E1%85%AE%E1%86%BA

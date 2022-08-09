# Q. SASS(SCSS)를 사용해본 적이 있나요? 기존 CSS와 비교할 때 어떤 면이 더 좋은가요?

## 1. 질문의 의도
CSS의 단점을 바탕으로 SASS(SCSS)를 쓰는 이유를 알고 있는가?

## 2. 개념 설명

### SASS(SCSS) 무엇인가?

✨ 이름을 풀어보면...
- SASS(Syntactically Awesome Style Sheets): 문법적으로 기가막히게 좋은 스타일 시트 
- SCSS(Sassy CSS): 멋진 CSS

✨ 공식 홈페이지에 적혀있는 SASS에 대한 설명을 보면...  
- CSS with superpowers (슈퍼파워를 가진 CSS)  
- Sass is the most mature, stable, and powerful professional grade CSS extension language in the world.  
(Sass는 세계에서 가장 성숙하고 안정적이며 강력한 전문가급 CSS 확장 언어입니다.)  

✨ 결론
- **CSS 확장 전처리기 언어**
- 코드의 재활용성을 올리고, 가독성을 올리는 등 CSS에서 보이던 단점을 보완하고, 개발의 효율을 올리기 위해 등장한 CSS 전처리기 언어이다.
- CSS를 편리하게 사용할 수 있도록 하며 추가 기능 또한 있는 확장판 스크립트 언어라고 보면 된다.

✨ CSS의 단점  
- 선택자(Selector)을 만들때 매번 불필요한 부모요소 선택자를 적어야 한다.
- function 같은게 없으니, 규모가 큰 프로제트의 경우 자동화하기 어렵고 모든 것을 수동으로 변경해야 한다.
- 결국 중복되는 코드가 많아 코드 줄수가 길어져 유지보수하기 어렵다.

> SCSS와 SASS의 차이  
> https://www.geeksforgeeks.org/what-is-the-difference-between-scss-and-sass/  
> https://www.interviewbit.com/blog/sass-vs-scss/

### CSS 전처리기(Preprocessor) 언어

- ex. Sass, Less, stylus
- CSS 문법과 굉장히 유사하지만 선택자의 중첩(Nesting)이나 조건문, 반복문, 다양한 단위(Unit)의 연산 등 CSS보다 훨씬 많은 기능을 사용해서 편리하게 작성할 수 있다.
- 따라서, 코드 작성에 드는 시간을 줄여주고, 코드를 유지 관리하는데 도움이 된다.
- 직접 동작시키는 것은 아니고, CSS로 컴파일 후 웹에서 동작시킨다. (자바스크립트와 타입스크립트의 관계와 비슷하다.) 

### SASS(SCSS)의 장점

- CSS보다 심플한 표기법으로 CSS를 구조화하여 표현할 수 있다.
- 즉, 가독성과 재사용성을 높여주어 유지보수가 쉬워지게 도와준다.
- 스킬 레벨이 다른 팀원들과의 작업 시 발생할 수 있는 구문의 수준 차이를 평준화할 수 있다.
- CSS의 태생적 한계를 보완하기 위해 Sass는 다음과 같은 추가 기능과 유용한 도구들을 제공한다.
  - 변수의 사용
  - 조건문과 반복문
  - Import (모듈화)
  - Nesting (선택자 반복 작성 줄여주는 기능)
  - Mixin (함수 개념)
  - Extend/Inheritance (확장/상속)
- 선택자의 중첩(Nesting)을 통해 반복되는 부모요소 선택자 사용을 줄일수 있다.
- 변수(Variable)을 사용해서 CSS 속성값을 통일해서 관리할 수 있다.
- 프로그래밍 언어에서 사용하는 조건문, 반복문을 통해서 동적으로 CSS 관리가 가능하다.
- 상속되는 선택자를 계층적으로 명시하여 불필요한 반복적 사용을 줄일 수 있다.

### SASS(SCSS)의 단점
- 전처리기를 위한 도구 필요
- 컴파일 시간 소요

## 3. 답변

SASS(SCSS)는 CSS의 전처리기 스크립팅 언어로, 변수, 중첩, 모듈화, mixins, extend, 연산 등의 기능이 있습니다.
이러한 기능들을 통해 CSS보다 재사용으로 인한 효율적인 코드 관리가 가능하고 가독성과 유지 관리가 쉽습니다.

🔗 참고 자료
- https://sass-lang.com
- https://inpa.tistory.com/entry/SCSS-%F0%9F%92%8E-SassSCSS-%EB%9E%80-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%BB%B4%ED%8C%8C%EC%9D%BC#CSS_%EC%99%80_Sass(SCSS)

<hr>

### Sass Basics
(아래는 SCSS 문법으로 작성한 예시입니다.)

1) Variables: 재사용하려는 정보가 있을 때

```
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

2) Nesting: HTML의 계층 구조와 동일하게 CSS 선택자를 중첩할 수 있다.
```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

3) Partials & 4) Modules: CSS를 모듈화함으로써 유지 관리를 더 쉽게 한다.

(부분 파일은 앞에 _를 붙인다.)
```
// _base.scss 
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
(@use 규칙을 통해 다른 SASS 파일을 모듈로 로드한다.)
```
// styles.scss
@use 'base';

.inverse {
  background-color: base.$primary-color;
  color: white;
}
```

5) Mixins: (연관성은 없지만) 재사용하는 CSS 그룹이 있을 때 (변수를 통해 값을 전달할 수도 있다.) / include한 class에 스타일을 복제

@mixin으로 선언
@include로 적용
```
@mixin theme($theme: DarkGray) {
  background: $theme;
  box-shadow: 0 0 1px rgba($theme, .25);
  color: #fff;
}

.info {
  @include theme;
}
.alert {
  @include theme($theme: DarkRed);
}
.success {
  @include theme($theme: DarkGreen);
}
```

6) Extend/Inheritance: (연관성이 있으면서) 재사용하는 CSS 그룹이 있을 때 (변수 사용 불가능)

%으로 선언
@extend로 적용
```
/* This CSS will print because %message-shared is extended. */
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

// This CSS won't print because %equal-heights is never extended.
%equal-heights {
  display: flex;
  flex-wrap: wrap;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
```

> mixin와 extend의 차이: https://www.geeksforgeeks.org/include-vs-extend-in-sass/

7) Operators: 연산(+, -, *, math.div(), %)
```
@use "sass:math";

.container {
  display: flex;
}

article[role="main"] {
  width: math.div(600px, 960px) * 100%;
}

aside[role="complementary"] {
  width: math.div(300px, 960px) * 100%;
  margin-left: auto;
}
```

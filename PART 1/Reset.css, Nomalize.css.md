# Reset.css, Normalize.css에 대해 설명해주세요

## 1. 질문의 의도

스타일을 수정하는 기법들을 알고있는가?

## 2. 개념

크롬, 사파리, IE등 각 브라우저마다 HTML요소의 기본 스타일을 가지고 있다. 따라서 CSS로 스타일링 할때 이러한 특징이 동일한 스타일 적용을 방해하기 때문에 이를 해결하기 위해 나온 스타일 초기화 기법들이다.

### Reset.css

모든 브라우저 내장 스타일을 없애는 기법으로, 그 어떤 스타일도 없는 상태에서 스타일링을 시작한다. h1~h6,p,em등 각 태그에 적용되는 스타일을 모두 없앤다. 보통 초기화를 한 후 각자의 방식에 맞게 변형해서 사용한다.

### Normalize.css

모든 브라우저의 스타일을 동일하게 하는 기법으로, 스타일을 없애는 Reset.css와 다르게 기존 스타일을 유지하되 브라우저들의 다른 스타일을 고치는 방식이다. 즉. 모든 브라우저의 스타일을 통일시키는 것이다.

## 3. 답변

브라우저들 마다 각각의 기본 CSS 스타일이 있는데, 이러면 일관성이 없어져 스타일을 적용할때 방해가 되기때문에 이를 해결하기 위해 나온 기법들이다. Reset.css는 모든 브라우저 내장 스타일을 없앤다. Normalize.css는 브라우저끼리의 공통의 스타일을 적용시킨다. 이 기법들을 사용하면 크로스 브라우징이 가능해진다.(모든 브라우저에서 깨지지 않고 의도한대로 올바르게 나오게 하는 작업) 각자 상황에 맞게 사용하면된다.

# 출처

- https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/css/reset-normalize.md

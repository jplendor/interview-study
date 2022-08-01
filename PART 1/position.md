# CSS에서 position이란?

## 1. 질문의 의도

CSS에서 자주 사용하는 position을 사용할 수 있는가?

## 2. 개념

position 속성은 문서 상에 요소를 배치하는 방법을 지정합니다.

- static : 요소를 일반적인 문서 흐름에 따라 배치합니다.
- relative: static + 자신을 기준으로 top, right, bottom, left의 값에 따라 오프셋을 적용합니다. 오프셋이란 top, left, right, bottom의 값을 의미하고 기준이 되는 곳으로부터 얼만큼 떨어져있는지를 나타내기 위해 필요한 속성입니다.
- absolute: 요소를 일반적인 문서 흐름에서 제거하고, 가장 가까운 위치 지정 조상 요소에 대해 상대적으로 배치합니다.
- fixed: 요소를 일반적인 문서 흐름에서 제거하고, 뷰포트의 초기 컨테이닝블록을 기준으로 삼아 배치합니다.
- sticky: static + fixed 특징을 동시에 가집니다. fixed는 뷰포트에 고정하지만, sticky는 scroll 박스에 고정합니다. scroll 박스는 overflow: auto 또는 overflow: scroll 속성을 적용한 가장 가까운 조상 박스입니다.

## 3. 답변

position 속성은 html 문서 상에서 요소가 배치되는 방식을 결정합니다. 기본값인 `static`은 html 문서 상에서 원래 있어야하는 위치에 배치됩니다. `relative`는 요소를 원래 위치를 기준으로 상대적으로 배치해줍니다. top, bottom, left, right 속성을 통해 위치 지정을 할 수 있습니다. `absolute`는 요소를 일반적인 문서 흐름에서 제거하고 해당 요소의 배치 기준을 상위 요소에서 찾습니다. 이때 상위 요소는 position 속성이 static이 아닌 첫 번째 상위 요소가 배치 기준으로 설정이 됩니다. `fixed`는 요소를 일반적인 문서 흐름에서 제거하고 배치 기준이 자신이나 부모요소가 아닌 뷰포트(브라우저 전체화면)입니다. 배치된채로 고정이 됩니다. `sticky`는 scroll 박스를 기준으로 배치되어 고정이됩니다. scroll 박스를 벗어나면 고정이 일어나지 않습니다. scroll박스는 overflow: auto 또는 overflow: scroll 속성이 적용된 가장 가까운 조상 박스입니다.

# 출처

- https://www.daleseo.com/css-position/
- https://tech.lezhin.com/2019/03/20/css-sticky
- https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/position.md#gear-%EC%98%A4%ED%94%84%EC%85%8B

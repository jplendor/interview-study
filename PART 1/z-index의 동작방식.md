# z-index의 동작방식에 대해 설명해주세요.

## 1. 질문의 의도

z-index와 쌓임 맥락에 대해 이해하고있는가?

## 2. 개념

### z-index와 쌓임 맥락

z-index를 이해하기 위해선 먼저, 쌓임 맥락(Stacking Context)의 개념을 이해해야 한다. 쌓임 맥락이란, HTML 요소들에 사용자를 바라보는 기준으로 가상의 z축을 생성하여 3차원으로 보는 것 이다. 따라서, 쌓임 맥락을 형성한다는 것은 자신만의 3차원 공간을 형성하는 것이며 그 요소들의 우선순위를 z-index가 정하게 되는 원리이다.

<img src="https://velog.velcdn.com/images%2Fkimdlzp%2Fpost%2Fa1bd98da-091b-40fb-a602-6e9244d3bbf4%2Fstacking%20context.png">

위 그림을 보면, z-index에 따라 쌓이는 것을 볼 수 있다. 이것이 쌓임 맥락의 개념이다. 쌓임 맥락을 형성하는 조건은 꽤 많다.

- position이 relative/absolute이면서 z-index가 auto가 아닌 요소
- position이 fixed/sticky인 요소
- opacity가 1보다 작은 요소
- transform이 none이 아닌 요소

쌓임 맥락은 다음 특징들을 갖는다.

- 쌓임 맥락은 다른 쌓임 맥락을 포함할 수 있다.
- 쌓임 맥락에서 쌓임을 고려하는 것은 오직 자식 요소들에 대해서 만이다.

즉, 2개의 쌓임 맥락을 형성하는 요소가 있다고 했을 때, 각각은 독립적인 쌓임 맥락을 가지며 그 안의 자식 요소들은 부모 안에서의 쌓임만 고려된다는 것이다.

### 우선순위

쌓임 맥락을 형성하는 요소가 아무것도 없다고 하면 다음 우선수위로 쌓이게 된다.
<img src="https://velog.velcdn.com/images%2Fkimdlzp%2Fpost%2Fc9719288-7fd4-41bd-a4b6-20e09b7ae975%2Fdefault%20stacking%20order.png">

```html
<div>1</div>
<div>2</div>
<div>
  3
  <div>4</div>
  <div>5</div>
  <div>6</div>
</div>
```

마크업이 이런식으로 되어있으면

<img src="https://velog.velcdn.com/images%2Fkimdlzp%2Fpost%2Fc6365ed8-379a-41c5-b55b-b62c54a40bec%2Fz-index%20stacking%20order.png">

이런식으로 쌓이게 된다.

- div1과 div2, div3은 같은 레벨(동등한 위치의 마크업) z-index에 따라 쌓이기 때문에 div2 > div3 > div1 순으로 쌓인다.
- div4와 div5, div6은 div3안에 있으므로 그 안에서 z-index에 따라 쌓인다.
- 즉, div3 안의 요소들의 z-index가 div1, div2 보다 커도 영향을 주지 않는다.
- 결론적으로 div5> div6 > div4 순으로 쌓인다.

결론적으로, 마크업 순서와 z-index를 모두 고려하여야 배치가 이루어진다.
z-index를 설정할 수 없는 요소들의 경우 (ex: position: absolute) 마크업 순서에 따라 쌓인다.

```html
<div>A</div>
<div>B</div>
<div>C</div>

div { position: absolute; }
```

여기서는 마크업 순서인 A,B,C 순으로 쌓임이 형성된다.

## 3. 답변

z-index의 동작 방식은 디스플레이 화면(뷰포트)와 사용자 사이에 가상의 z축을 생성하여 3차원으로 쌓이는 개념을 쌓임 맥락이라고한다. 이 쌓임 맥락은 z-index에 따라 우선순위가 결정된다. 그렇지만 z-index가 절대적인 기준이 되어 우선순위가 만들어지지는 않는다. 부모, 자식 관계 및 마크업 순서(HTML뼈대 구조에 따라)등을 고려하여 쌓임 맥락의 우선순위가 결정된다.
즉, html태그를 먼저 비교해서 동일 레벨에 있으면 그때 z-index를 비교하여 쌓임 맥락의 우선순위가 정해지는 것이다.

# 출처

- https://velog.io/@kimdlzp/z-index%EC%9D%98-%EB%8F%99%EC%9E%91-%EB%B0%A9%EC%8B%9D

# Q. ```<sciprt>```태그 속성인 async, defer의 차이, 실행 순서에 대해 설명해주세요.

## 1. 질문의 의도
```<sciprt>```태그 속성인 async, defer에 대해 알고 있는가? 

## 2. 개념 설명

### async와 defer의 필요성
- 브라우저가 HTML을 로드하고 <script>...</script>태그를 발견하면 DOM 빌드를 계속할 수 없습니다. 
- 지금 바로 스크립트를 실행해야 합니다. 외부 스크립트도 마찬가지입니다 <script src="..."></script>. 브라우저는 스크립트가 다운로드될 때까지 기다려야 하고 다운로드한 스크립트를 실행해야 합니다.
- 그런 다음에만 나머지 페이지를 처리할 수 있습니다.

```HTML
<p>...content before script...</p>

<script src="https://javascript.info/article/script-async-defer/long.js?speed=1"></script>

<!-- This isn't visible until the script loads -->
<p>...content after script...</p>
```


**html 상단 혹은 중간에 script가 들어가 있을 경우 크게 두가지 문제가 생길 수 있다.**
- 스크립트는 그 아래에 있는 DOM 요소를 볼 수 없으므로 핸들러 등을 추가할 수 없습니다.
- 페이지 상단에 부피가 큰 스크립트가 있으면 "페이지를 차단"합니다. 사용자는 다음을 다운로드하여 실행할 때까지 페이지 콘텐츠를 볼 수 없습니다.

**위 두가지 문제가 발생하지 않도록 일반적으로 html 마지막줄에 script를 넣는다. 하지만, 이 방법도 완벽하지 않다.**
- 브라우저는 전체 HTML 문서를 다운로드한 후에만 스크립트를 인식하고 다운로드를 시작할 수 있습니다. 긴 HTML 문서의 경우 눈에 띄게 지연될 수 있습니다.

### defer
- 스크립트를 non-blocking으로 만든다.
- 브라우저는 HTML을 처리하고 DOM을 빌드하는 동시에 스크립트는 "백그라운드에서" 로드한 다음, DOM이 완전히 빌드되면 실행됩니다. 
- (그러나 DOMContentLoaded 이벤트 전에)
- 여러 개의 스크립트를 로드하는 경우, 로드하는 순서대로 실행된다.

```HTML
<p>...content before scripts...</p> ---1️⃣

<script>
  document.addEventListener('DOMContentLoaded', () => alert("DOM ready after defer!")); ---2️⃣
</script>

<script defer src="https://javascript.info/article/script-async-defer/long.js?speed=1"></script> ---3️⃣

<p>...content after scripts...</p> ---4️⃣
```

**실행결과**  
1️⃣, 4️⃣이 화면에 나타나고 => 3️⃣(script) => 2️⃣(DOMContentLoaded 이벤트)

### async
- 스크립트를 non-blocking으로 만든다.
- 브라우저는 HTML을 처리하고 DOM을 빌드하는 동시에 스크립트는 백그라운드에서 로드되고, 준비가 되면 실행됩니다. (DOM 빌드 및 기타 스크립트는 기다리지 않는다.)(실행되는 동안은 파싱 중단)
- (DOMContentLoaded 이벤트 전후, 보장 없음)

```
<p>...content before scripts...</p> ---1️⃣

<script>
  document.addEventListener('DOMContentLoaded', () => alert("DOM ready!")); ---2️⃣
</script>

<script async src="https://javascript.info/article/script-async-defer/long.js"></script> ---3️⃣
<script async src="https://javascript.info/article/script-async-defer/small.js"></script> ---4️⃣

<p>...content after scripts...</p> ---5️⃣
```

**실행결과**  
2️⃣️(DOMContentLoaded 이벤트) => 1️⃣, 5️⃣이 화면에 나타나고 => 4️⃣(small) => 3️⃣(long)

## 3. 답변
script는 파싱을 차단하는 리소스이기 때문에, html 중간에 script 태그를 만나면 파싱이 중단되고, script 다운로드 및 실행이 이루어진다. 
이는 스크립트의 실행이 완료될 때까지 html 파싱이 중단된다는 문제가 있고, script에서 dom을 참조 에러가 발생할 수 있다.
그래서 script를 html 가장 마지막에 넣거나, defer, async와 같은 속성을 사용하여 script를 non-blocking하게 만들 수 있다.
defer, async는 파싱되는 동시에 다운로드 된다는 공통점이 있으나, 실행 시점에 차이가 있다.
defer은 html 파싱이 다 끝났을 때 실행된다.
async는 다운로드되는 즉시 실행된다.

🔗 참고 자료
- https://webroadcast.tistory.com/15
- https://javascript.info/script-async-defer

# DOCTYPE은 무엇을 하나요?

1. 질문의 의도  
   html파일에 기본적으로 사용되는 DOCTYPE에 대해 개념을 알고 코드를 짜는가?

2. 개념 설명  
   DOCTYPE은 document type의 약어입니다. DOCTYPE은 항상 DTD(Document Type Definition)와 관련됩니다.
   <br>  
   DTD는 특정 문서가 어떻게 구성되어야 하는지 정의합니다. 예를들어 `<button>`는 `<span>`를 포함할 수 있지만, `<div>`는 그럴 수 없다. 반면, DOCTYPE은 문서가 존중할만한 DTD를 선언합니다. 예를들어 이 문서는 HTML DTD를 존중한다. 
   <br>  
   웹 페이지는 DOCTYPE 선언이 필요합니다.
   <br>  
   HTML5 표준에 대한 DOCTYPE 선언은 `<!DOCTYPE html>`입니다.
3. 답변  
   DOCTYPE html이란 웹문서가 어떤 버전의 HTML 언어로 작성되었는지 결정하는 기능입니다.  
   DTD(특정 문서가 어떻게 구성되어야 하는지)를 통해서 현재의 웹문서가 어떤 버전의 HTML 기술로 작성되었는지 웹브라우저에 전달합니다.  
   브라우저는 선언된 문서 버전에 맞는 HTML 기술로 페이지를 로드합니다.  
   선언하는 이유는 HTML 버전마다 적용되는 태그가 있고, 적용되지 않는 태그가 있습니다. 그래서 HTML의 버전을 선언하여 어떤 버전을 사용할 것인지 결정하는 역할을 합니다.
### 출처
https://www.frontendinterviewhandbook.com/kr/html-questions#doctype%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%84-%ED%95%98%EB%82%98%EC%9A%94
<br>
https://dasima.xyz/doctype-html/

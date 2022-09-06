# Q. 왜 일반적으로 CSS <link> 태그를 <head></head> 태그 사이에 위치시키고, JS <script> 태그를 </body> 직전에 위치시키는 것이 좋은 방법인가요? 다른 예외적인 상황을 알고있나요? 

## 1. 질문의 의도
웹 브라우저의 처리 순서를 이해하고 있는가?

## 2. 개념 설명

## 3. 답변

✨ ```</link>를 <head> 안에 넣는 이유``` 

```<link>```를 ```<head>``` 안에 넣는 것은 최적화된 웹사이트를 구출할 때 적절한 명세의 일부입니다. 페이지가 처음로드되면 HTML과 CSS가 동시에 파싱됩니다.  
HTML은 DOM(Document Object Model)을 만들고 CSS는 CSSOM (CSS Object Model)을 만듭니다.  
두 가지 모두 웹사이트에서 시각적인 부분을 만드는데 필요하므로, 빠른 "first meaningful paint"를 가능하게 합니다. 
이 점진적 렌더링은 사이트의 성능 점수에서 측정되는 사이트 최적화의 범주입니다. 문서 최하단에 스타일시트를 두는 것은 많은 브라우저에서 점진적 렌더링을 금지하게 되는 것입니다.  
몇몇 브라우저는 스타일이 변경되면 페이지의 요소를 다시 그리는 것을 피하기 위해 렌더링을 차단합니다. 그렇게되면 사용자는 빈 하얀 페이지를 보게됩니다. 

그 외에도 상단에 배치하면 페이지가 점진적으로 렌더링되기 때문에 UX가 향상됩니다. 문서 맨 아래에 CSS 를 두는 것은 Internet Explorer 를 비롯한 많은 브라우저에서 점진적 렌더링을 금지시키는 것입니다. 몇몇 브라우저는 스타일이 변경되면 페이지의 요소를 다시 그리지 않아도 되도록 렌더링을 차단합니다. 사용자는 빈 하얀 페이지에서 멈추게 됩니다. 또한 스타일이 없는 내용이 잠깐 보이는 것을 방지합니다. 다른 경우에는 스타일되지 않은 내용이 깜빡일 수 있습니다(flashes of unstyled content: FOUC).

✨ ```</body> 직전에 <script>를 넣는 이유```  

```<script>```는 다운로드되고 실행되는 동안 HTML 파싱을 차단합니다. 스크립트를 맨 아래에 두면 HTML을 먼저 파싱하여 사용자에게 표시할 수 있습니다.  

스크립트에 ```document.write()```가 있을 때는 ```<script>```를 아래쪽에 두는 것이 예외적일 수 있습니다만, 요즘은 ```document.write()```를 사용하지 않는 것이 좋습니다.  
또한, ```<script>```를 맨 아래에 두면, 브라우저가 전체 문서가 파싱될 때까지 스크립트 다운로드를 시작할 수 없다는 것을 의미합니다.  
이렇게하면 DOM 요소를 조작해야하는 코드가 오류를 발생시키지 않고 전체 스크립트를 중지시키지 않습니다.  
```<head>```에 ```<script>```를 넣어야하는 경우, defer 속성을 사용하세요. HTML을 파싱한 후에 스크립트를 다운로드하고 실행하는 것과 같은 효과가 있습니다.  
 
  
  
🔗 참고 자료
- https://www.frontendinterviewhandbook.com/kr/html-questions#%EC%99%9C-%EC%9D%BC%EB%B0%98%EC%A0%81%EC%9C%BC%EB%A1%9C-css-link-%ED%83%9C%EA%B7%B8%EB%A5%BC-headhead-%ED%83%9C%EA%B7%B8-%EC%82%AC%EC%9D%B4%EC%97%90-%EC%9C%84%EC%B9%98%EC%8B%9C%ED%82%A4%EA%B3%A0-js-script-%ED%83%9C%EA%B7%B8%EB%A5%BC-body-%EC%A7%81%EC%A0%84%EC%97%90-%EC%9C%84%EC%B9%98%EC%8B%9C%ED%82%A4%EB%8A%94-%EA%B2%83%EC%9D%B4-%EC%A2%8B%EC%9D%80-%EB%B0%A9%EB%B2%95%EC%9D%B8%EA%B0%80%EC%9A%94-%EB%8B%A4%EB%A5%B8-%EC%98%88%EC%99%B8%EC%A0%81%EC%9D%B8-%EC%83%81%ED%99%A9%EC%9D%84-%EC%95%8C%EA%B3%A0%EC%9E%88%EB%82%98%EC%9A%94
- https://developer.mozilla.org/en-US/docs/Glossary/first_meaningful_paint

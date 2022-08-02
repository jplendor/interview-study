# margin과 padding에 대해 설명하세요

## 1. 질문의 의도

css를 할때 자주 다루는 margin과 padding에 대해 알고있는가?

## 2. 개념 설명

- margin은 바깥쪽 여백, padding은 안쪽 여백을 의미합니다.   
- margin과 padding은 border를 경계로 나뉩니다.     

- box-sizing: content-box => width = content 너비
- box-sizing: border-box => width = padding + border + content 너비

### box-model
![image](https://user-images.githubusercontent.com/97583339/182293468-c6f89e24-6a1d-4acb-a263-339124b9e0c9.png)

### 마진 병합(collapsing margins)
마진 병합이란 인접한 공간에 margin-bottom과 margin-top 속성을 적용할 경우에 두 속성 중 큰 속성값이 작은 속성값을 병합하는 현상을 말합니다.   
자주 마주치는 마진 병합 현상에는 형제간에 발생하는 마진 병합 현상, 부모 자식 간에 발생하는 마진 병합 현상이 있습니다.  
마진 병합은 상하에서만 일어나는 현상으로 margin-left와 margin-right에서는 발생하지 않습니다. 따라서 Block 요소의 성격을 갖고 있는 태그에서만 발생합니다.  

- 형제간에 발생하는 마진 병합 현상

index.html
```
<div id=“first”></div>
<div id=“second”></div>
```
style.css
```
#first {
    width: 100%;
    height: 200px;
    background-color: yellow;
    margin-bottom: 100px;
}

#second {
    width: 100%;
    height: 200px;
    background-color: blue;
    margin-top: 50px;
}
```
first margin-bottom 100px + seconde margin-top 50px = 150px이 아니고, 큰 값이 작은 값을 병합하여 100px이 된다. 
![image](https://user-images.githubusercontent.com/97583339/182294814-ba1ce21b-5f07-470d-aed9-2a74567d6dbe.png)

- 부모 자식 간에 발생하는 마진 병합 현상 (자식의 margin-top 속성이 부모에게 영향을 미치는 것)

index.html
```
<div id=“parent”>
    <div id=“child”></div>
</div>
```

style.css
```
#parent {
    width: 100%;
    height: 500px;
    background-color: yellow;
}
 
#child {
    width: 300px;
    height: 300px;
    background-color: blue;
    margin-top: 100px;
}
```
child만 100px 아래로 내려가야하는데, parent도 같이 100px 아래로 내려간다.
![image](https://user-images.githubusercontent.com/97583339/182299919-2d7a79e1-b8a8-4b3f-9dc7-a2197af03acf.png)

=> position으로 해결가능하다.

## 3. 답변

margin은 바깥쪽 여백, padding은 안쪽 여백을 의미합니다. border를 경계로 나뉩니다.

🔗 참고 자료
- https://www.w3schools.com/css/css_boxmodel.asp
- https://thebook.io/006943/ch03/07/03-01/

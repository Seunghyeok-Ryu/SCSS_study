# SCSS
- SCSS, CSS 연습 사이트
<a href = "https://www.sassmeister.com/">sassmeister</a>
---

## 주석
- 두 가지 종류의 주석
  - /* */
  - //
```scss
.container{
  h1 {
    color: red;
    /* background-color: orange; */
    // font-size: 80px;
  }
}
```
- scss를 css로 컴파일시
  - /* */의 주석 내용은 존제
  - // 의 주석 내용은 삭제
```css
.container h1 {
  color: red;
  /* background-color : orange; */
}
```
---
## 중첩 기능
- SCSS
```scss
.container{
  > ul{   // 자식 선택자 선택시 화살표 후 띄어쓰기 (> ul)
    li {
      font-size : 40px;
      .name{
        color : royalblue;
      }
      .age {
        color : orange;
      }
    }
  }
}
```
- CSS
```css
.container > ul li {
  font-size: 40px;
}
.container > ul li .name {
  color: royalblue;
}
.container > ul li .age {
  color: orange;
}
```
---
## 상위(부모) 선택자 참조
- & 기호 사용
  - 자신이 포함된 그 영역의 상위 선택자를 참조
  - 상위 선택자가 하위 선택자의 &기호로 치환
- SCSS
```scss
.fs {
    &-small { font-size : 12px; }
    &-medium { font-size : 14px; }
    &-large { font-size : 16px; }
}
```
- CSS
```css
.fs-small {
  font-size: 12px;
}
.fs-medium {
  font-size: 14px;
}
.fs-large {
  font-size: 16px;
}
```
---
## 중첩된 속성
- 선택자 처럼 사용하나 : 기호를 붙여줘야함
- 중괄호{}가 끝나는 부분에 ; 기호를 붙여줘야 함
- 네임스페이스 : (font-weight/size/family..., margin top/left/bottom..) 속성 부분의 이름이 동일한 것.
<br>
<br>
- SCSS
```scss
.box {
    font : {
        weight: bold;
        size: 10px;
        family: sans-serif;
    };
    margin : {
        top : 10px;
        left : 20px;
    };
    padding: {
        top: 10px;
        bottom : 40px;
        left : 20px;
        right : 30px;
    };
};
```
- CSS
```css
.box {
  font-weight: bold;
  font-size: 10px;
  font-family: sans-serif;
  margin-top: 10px;
  margin-left: 20px;
  padding-top: 10px;
  padding-bottom: 40px;
  padding-left: 20px;
  padding-right: 30px;
}
```
---

## 변수
- $변수 : 내용 ; 를 통해 변수 선언
- 선언된 범위에서 유효 범위를 가짐

- SCSS
```scss
.container {
  $size : 100px;
  position : fixed;
    top : $size;
    .item {
      $size : 200px;  // $size 값 재할당
        width : $size;
        height : $size;
        transform : translateX(100px);
    }
}
.box {
  width : $size;
   // error발생 :
   // $size 변수는 .container 내부에서 선언 되었기에 외부에서 사용 불가(유효 범위)
}
```
- CSS
```css
.container {
  position: fixed;
  top: 100px;
}
.container .item {
  width: 200px;
  height: 200px;
  transform: translateX(100px);
}
```
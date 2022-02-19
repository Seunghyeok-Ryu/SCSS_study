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
---

## 산술 연산자
- SCSS
```scss
div {
    $size : 30px ;
    width : 20px + 20px;
    height : 40px - 10px;
    font-size : 10px * 2;
    margin : 30px / 2;  // 단축 속성을 지칭하는 / 기호로 나누기 연산이 되지 않음
    // 1.괄호를 이용한 방법
    margin : (30px / 2);
    // 2. 변수를 이용한 방법
    margin : $size / 2;
    // 3. 다른 산술연산자를 같이 쓰는 방법
    margin : 10px + 10 / 2;
    padding : 20px % 7;
}
```

- CSS
``` CSS
div {
  width: 40px;
  height: 30px;
  font-size: 20px;
  margin: 15px;
  margin: 15px;
  margin: 15px;
  padding: 6px;
}
```
---

## 재활용
- 다시 사용할 코드를(@mixin 이름)을 통해 설정
- (@include 이름) 을 통해 사용

- SCSS
```scss
@mixin box($size:80px, $color : tomato) { // @mixin을 통해 변수 설정 및 기본 값 설정 가능
    width : $size;
    height : $size;
    background-color : $color;
}
.container {
    @include box(200px, blue);  // @include를 통해 설정 된 변수의 값들 사용(기본 값 재할당 가능)
    .item {
        @include box($color : green);
        // 키워드 인수
        // 재할당 시 순서대로 입력해야 하나 키워드를 통해 원하는 값만 재할당 가능
    }
}

.box {
    @include box;
}
```

- CSS
```CSS
.container {
  width: 200px;
  height: 200px;
  background-color: blue;
}
.container .item {
  width: 80px;
  height: 80px;
  background-color: green;
}

.box {
  width: 80px;
  height: 80px;
  background-color: tomato;
}
```
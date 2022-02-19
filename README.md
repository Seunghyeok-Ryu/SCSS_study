# SCSS
- SCSS, CSS 연습 사이트
<a href = "https://www.sassmeister.com/">sassmeister</a>

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

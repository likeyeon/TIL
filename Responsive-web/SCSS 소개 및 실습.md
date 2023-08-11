# #3 - SCSS 소개 및 실습
본 내용은 반응형 웹 만들기 수업을 토대로 작성였습니다.

## SCSS
**사용방법**
 - scss 파일은 브라우저에서 읽을 수 있는 파일이 아니므로, 작성 후 컴파일하여 css 파일로 변환시켜줘야 함.
   
**변수**
- `$` 사용하여 변수 할당 & 사용
 ```scss
  $font: Helvetica, sans-serif;
  $primary-size: 20px;
  $value: Calc(100% - 20px);
  
  .variable-test {
    font-family: $font;
    font-size: $primary-size;
    width: $value;
  }
  ```
**네스팅**
- 중첩을 사용하여 스타일 지정 가능
- 다만, 지나친 중첩은 피하는 것이 좋음
```scss
.menu {
  width: 600px;
  height: 40px;
  background-color: blue;

  >ul {
    padding: 0;
  }

  li {
    color:white;
  }
}
```

**모듈**
- 부분적인 sass파일을 생성하여 모듈화 할 수 있음
- _partial.scss와 같이 파일을 작성할 수 있음
- 해당 파일은 sass가 컴파일하지 않음
- 만들어진 파일은 `@use` 규칙으로 사용
```css
@use "util" as remUtil;

.menu {
  width: remUtil.rem(600px);
}
```

**확장/상속(expand)**
- sass 에서 특정 선택자를 상속 할 때, `@extend` 지시자를 사용한다.
```scss
// 작성 방법 : @extend .클래스명; 또는 @extend %클래스명;
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}
```

**믹스인(mixin)**
- 믹스인은 코드블럭을 재사용하기 위한 도구
- 함수처럼 특정 속성값을 인자로 전달하여 사용할 수 있음
- mixin을 선언 할 때는 `@mixin` 지시자를 사용하며, 적용할 때는 `@include` 지시자를 사용한다.
```scss
// 작성 방법
// 선언 : @mixin mixin명{}
// 적용 : @include mixin명 또는 @include mixin(전달할 인자)

@mixin theme($theme: DarkGray, $fontColor: #fff) {
  background: $theme;
  color: $fontColor;
}

.info {
  @include theme;
  // css 파일
  // background: DarkGray;
  // color: #fff;
}

.alert {
  @include theme($theme: DarkRed, $fontColor: skyblue);
  // css 파일
  // background: DarkRed;
  // color: skyblue;
}

.success {
  @include theme($theme: DarkGreen);
  // css 파일
  // background: DarkGreen;
  // color: #fff;;
}
```

**연산자**
- SCSS에서 사칙연산이나 논리연산과 같은 연산을 할 수 있음
- 상단에 `@use "sass:math";` 선언
   
**함수**
- SCSS 내의 복잡한 계산과정을 재사용 할 수 있게 해줌
- `@function` 사용하여 함수 선언

## 참고
- [불러오기, 상속, 믹스인 관련 SCSS 문법](http://megaton111.cafe24.com/2017/01/13/sass-%EB%AC%B8%EB%B2%95-%EB%B6%88%EB%9F%AC%EC%98%A4%EA%B8%B0import-%EC%83%81%EC%86%8Dextend-%EB%AF%B9%EC%8A%A4%EC%9D%B8mixin/)
- 공식문서 : https://sass-lang.com/documentation/

# #1 - 반응형 웹
본 내용은 반응형 웹 만들기 수업을 토대로 작성였습니다.

## 반응형 웹
> 디바이스의 크기에 따라 웹페이지의 크기가 자동적으로 재조정되는 것

**이점**
- 장치 호환성
- 일관된 사용자 경험
- 유지보수

**고려할 점**
- 화면 구성에 대한 고민 필요
- 넓이가 넓다고 무조건 정보를 더 보여주거나, 넓이가 좁다고 무조건 정보를 가리는 것만이 정답이 아님
    - UXUI를 고려하며 화면 크기에 따라 어떤 컨텐츠를 보여줄지 고려

## 뷰포트

> https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag
> <br/>브라우저 창에서 문서를 볼 수 있는 부분을 포함하는 창 영역

**뷰포트 메타 태그**
```
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
1. `width`
    - viweport 너비 설정
    - `width=600` 같이 특수 값으로 설정 가능. (너비는 px 단위이며 meta 태그에서는 단위를 생략)
    - `width=device-width` : 브라우저 너비를 장치 너비에 맞추어 표시
2. `height`
    - viewport 높이 설정
    - `height=600` 같이 width와 동일한 방식으로 특수 값 설정 가능
    - `height=device-height` : 브라우저 높이를 장치 높이에 맞추어 표시
3. `initial-scale`
    - 페이지가 처음 로드될 때 확대/축소 수준을 제어 (zoom 레벨 설정)
    - 기본값: 1, 최소: 0.1, 최대: 10 
4. `minimum-scale`, `maximum-scale`
    - 페이지에서 허용되는 확대 정도, 축소 정도를 제어
    - 최소: 0.1. 최대: 10. 기본값: 10. 음수 값: 무시됨.
5. `user-scalable`
    - 페이지에서 확대/축소 작업이 허용되는지 여부를 설정(yes, no, 1, 0)
    - ios에서는 접근성 향상을 위해 user-scalable 대신 핀치줌을 사용

## 미디어 쿼리

**CSS media query**

- 여러분이 지정한 규칙에 브라우저 및 장치 환경이 일치하는 경우에만 CSS를 적용할 수 있는 방법을 제공
- `media type` : all / print / screen
- `width`, `height` : 뷰포트의 넓이와 높이를 정확하게 지정
- `min-width`, `max-width`, `min-height`, `max-height` : 뷰포트의 최소, 최대 넓이와 높이를 지정
- `orientation` : 뷰포트의 눕힘 상태를 지정 ex) landscape, portrait
- 자바스크립트에서도 미디어 쿼리 이벤트를 캐치하여 스크립트 실행 가능
  - `matchMedia` : window 내장 메서드로, 파라미터로 string 형태의 미디어 쿼리를 받아서 <br/>**현재 document 가 해당 미디어 쿼리를 충족하는지 알 수 있는 MediaQueryList 객체를 반환**한다.
    <img width="529" alt="matchMedia" src="https://github.com/likeyeon/TIL/assets/94125863/b7f17a2d-bc43-4017-9d9b-8449c755856e">

    
```javascript
const mql = window.matchMedia(“(max-width: 640px)”);

mql.onchange((event) => {
  if (event.matches) {
    …
  } else {
    …
  }
})
```


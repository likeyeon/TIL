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

> 브라우저 창에서 문서를 볼 수 있는 부분을 포함하는 창 영역

**뷰포트 메타 태그**

- `content=width`
    - 뷰포트의 가로 사이즈를 조정.
    - device-width를 넣으면 기기 크기에 맞춰진다.
- `initial-scale`
    - 페이지가 최초 로드되었을 때 얼마나 줌이 되어있는지를 설정
    - `minimum-scale` : 페이지가 최소 얼마나 축소될 수 있는지 설정
    - `maximum-scale` : 페이지가 최대 얼마나 확대될 수 있는지 설정
    - `user-scalable` : 페이지가 확대/축소 될 수 있는지를 설정 (yes, no, 1, 0)
        - ios에서는 접근성 향상을 위해 핀치줌을 사용

## 미디어 쿼리

**CSS media query**

- 여러분이 지정한 규칙에 브라우저 및 장치 환경이 일치하는 경우에만 CSS를 적용할 수 있는 방법을 제공
- `media type` : all / print / screen
- `width`, `height` : 뷰포트의 넓이와 높이를 정확하게 지정
- `min-width`, `max-width`, `min-height`, `max-height` : 뷰포트의 최소, 최대 넓이와 높이를 지정
- `orientation` : 뷰포트의 눕힘 상태를 지정 ex) landscape, portrait
- 자바스크립트에서도 미디어 쿼리 이벤트를 캐치하여 스크립트 실행 가능
  - `matchMedia` : window 내장 메서드로, 파라미터로 string 형태의 미디어 쿼리를 받아서 **현재 document 가 해당 미디어 쿼리를 충족하는지 알 수 있는 MediaQueryList 객체를 반환**한다.
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

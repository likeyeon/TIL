# #2 - 상대단위와 레이아웃
본 내용은 반응형 웹 만들기 수업을 토대로 작성였습니다.

## CSS의 단위
- 절대 단위
  - 절대적이며 언제나 크기가 같은 단위
  - ex) px
- 상대 단위
  - 기준에 따라 크기가 변화하는 단위
  - % : 부모 요소 기준
  - em : 자신과 부모의 font-size가 기준
  - rem : 루트 엘리먼트의 폰트 사이즈가 기준
  - vw : 뷰포트의 가로 길이의 1%
  - vh : 뷰포트의 세로 길이의 1%
- rem과 em은 각각 언제?
  - 폰트 사이즈에 em을 사용하는 것은 원하지 않는 사이즈를 발생시킬 수 있고 추적이 힘듬. em보단 rem을 사용하는것이 적절.
- 타이포그래피 px? rem?
  - px을 사용시에 브라우저의 폰트크기 설정(root의 font size)이 변경을 따라가지 않음.
  - 따라서 웹 접근성을 생각한다면 타이포그래피에 px대신 rem을 쓰는 것이 바람직함.
  - **rem을 쓰지 않을 이유는 없음.**
- rem 불편함을 해결하기
  - 디자인 가이드가 px로 나온 경우, 일일히 계산하여 rem으로 넣어주는 것은 매우 불편
    - -> SCSS와 function 사용
    ```
    @function rem($value) {
      @return ($value / 16px) * 1rem
    }
    div {
      width: rem(400px);
    }
    ```
- Dynamic viewport
  - 모바일 브라우저의 뷰포트 이슈를 해결! <br/>
    <img src="https://github.com/likeyeon/TIL/assets/94125863/8ffcb774-db68-437a-855d-bd29d8531760" width="50%"/>

## Flex box
[이번에야말로 CSS Flex를 익혀보자](https://studiomeal.com/archives/197)
- order
  - order 속성이 있는 아이템이 order 속성 X 아이템보다 뒤로 감
  - order의 값이 -1이라면 무조건 제일 앞으로 감
  - 같은 값이라면 소스상 앞에 있는 아이템이 더 먼저 옴
- flex-grow
  - 컨테이너에서 할당 가능한 공간(빈 공간)을 얼마나 나누어 받을지 결정 (flex-grow 값에 따라 나눠받음)
- flex-shrink
  - 컨테이너에서 넘치는 아이템의 공간을 얼마나 나누어 받을지 결정 (flex-shrink 값에 따라 나눠받음)
 
## Grid
[이번에야말로 CSS Grid를 익혀보자](https://studiomeal.com/archives/533)
- grid-template-rows/columns
  - 각 행과 열의 크기를 정의함
  - 'fr'이라는 단위를 사용하여 사용 가능한 공간을 지정
- grid-gap
  - 행과 열 사이의 간격을 지정. px, em, rem등의 값을 사용
- grid-template-areas
  - 영역 이름으로 그리드 정의
- Flex VS Grid
  - Flex는 1차원 (한 방향으로의 축만 가짐)으로 나열되는 컨텐츠를 표현하는데 사용
    - ex) 카드식 컨텐츠 나열
  - Grid는 2차원 (가로와 세로 두 축을 가짐)으로 배치되는 컨텐츠를 표현하는데 사용 
    - ex) 레이아웃, 표, 여러 영역을 가지는 컨텐츠 배열
   
## SCSS 맛보기
- SCSS란?
  - SASS 3번째 버전에서 추가되었으며, SASS의 모든 기능을 지원하면서 CSS 구문과 완전히 호환되도록 만들어짐
  - 변수, 함수, 믹스인, 네스팅 등을 사용하여 더욱 효율적으로 코드를 작성할 수 있음
- 변수
  - 여러가지 값을 변수에 담아서 사용할 수 있다.
  - 변수 선언시 변수 이름은 $으로 시작
- 네스팅
  - 셀렉터를 html처럼 계층 구조로 사용할 수 있게 해줌
- @function
  - SCSS 내의복잡한 계산과정을 재사용 할 수 있게 해줌
- &
  - 같은 태그에 몇가지 부분만 다르다면 &. 속성으로 나누어 스타일을 주는 것

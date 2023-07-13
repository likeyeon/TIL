# #2 - Pages, Pre Rendring
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
## 1. pages
- NextJS는 **/pages 내의 파일명으로 자동 라우팅** 을 해준다.
  - 단, 해당 컴포넌트들은 `export default` 해야 함
  - 파일 내의 함수명은 파일명과 불일치해도 됨
  - ex) pages/about.js 생성 -> localhost:3000/about
- 예외 사항으로 **index.js는 앱의 홈(/)** 으로 연결된다.
  - localhost:3000 그 자체이므로 뒤에 /index를 붙이면 안됨
- JSX를 사용하여도 `import react from "react"`를 쓸 필요가 없다.
  - 단, useState, useEffect와 같은 react method를 사용하려면 import 해야 함
 
## 2. Pre Rendring
### React.js VS Next.js
- **Clinet Side Render(CSR)**
  - **비어있는 html을 가져온 후, 자바스크립트 코드를 요청** 하여 사용자에게 UI가 보이게 함
  - 로딩이 느린 유저의 경우, js 코드를 받아오기 전에 흰 화면을 오래 본다는 단점 존재
  - ex) React.js
- **Pre Rendering**
  - **컴포넌트의 초기상태를 기반으로 미리 렌더링된 실질적인 html 요소를 보여줌**
  - 생성된 html은 해당 페이지에 필요한 최소한의 자바스크립트 코드와 연결된다.
  - 그 후 브라우저에 의해 페이지가 로드되면, 자바스크립트 코드가 실행되어 페이지와 유저가 상호작용할 수 있게 된다.
  - 로딩이 느리거나 자바스크립트가 비활성화 되어도 화면을 볼 수 있음
  - ex) Next.js
    
### hyderation
  - HTML 코드와 React인 js코드를 서로 매칭 시키는 과정
  - pre-render된 페이지에 react의 반응성을 입혀 모든 기능이 동작하게 됨

# 참고
[Next.js의 렌더링 과정(Hydrate) 알아보기](https://www.howdy-mj.me/next/hydrate)

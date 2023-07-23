# #3 - Routing, Css Modules, Styles JSX
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
## 1. Routing
- a 태그를 네비게이팅에 사용하면 안되는 이유
  -  브라우저가 다른 페이지로 이동하기 위해 전체 페이지를 새로고침하기 때문
- NextJS 에서 제공하는 **&#60;Link&#62; 컴포넌트를 사용**한다.
  - a 태그를 Link 태그로 감싸고 href 를 넣어준다.
- router 관련 property, function을 사용하려면 useRouter Hook을 사용
- **⚠️ 13버전 변경 사항**
  - **Link 태그에 a 태그에서 사용하던 속성 적용 가능**
  - 네비게이팅 하고 싶다면 a 태그를 빼거나, **Link 태그 안에 legacyBehavior 를 추가**해야함
  ```
  <Link href="/" legacyBehavior><a>Home</a></Link>
  ```

## 2. CSS Modules
- **modules.css** 파일을 import
  - 자바스크립트 오브젝트에서의 프로퍼티 형식으로 사용
    - ex. `className={styles.이름}`
- 두 가지 이상 클래스 이름을 적용하고 싶다면?
  ```
  1) 벡틱 사용
     className = {`${styles.이름} ${styles.이름2}`}
  
  2) 배열로 묶어준 후, join(" ")을 통해 문자열로 바꿔줌
     className = [{styles.이름} {styles.이름2}.join(" ")]
  ```
- 장점
  - 페이지가 빌드될 때, NextJS가 클래스 이름을 무작위 랜덤 텍스트로 바꿔줌
    - -> 클래스 이름을 중복 고민 없이 얼마든지 재사용 가능
- 단점
  - css 모듈 파일을 따로 생성하고 수정하는 과정이 비효율적
  - 여러개의 class 선택자를 가지는 경우, 문법이 장황하여 가독성이 떨어짐

## 3. Styles JSX
- NextJS에서만 할 수 있는 스타일링 방법
- 컴포넌트에서 받은 props를 사용 가능
- 오직 컴포넌트 내부로 범위가 한정
  - 클래스 이름들이 무작위로 바뀌기 때문에, 다른 컴포넌트에서 이미 존재하는 동일한 클래스 이름을 사용해도 해당 style이 적용되지 않음
```
<style jsx>{`
  a {
    text-decoration: none;
  }
  .active {
    color: ${props.color};
  } 
`}</style>
```


## 참고
[Invalid `<Link>` with `<a>` child](https://nextjs.org/docs/messages/invalid-new-link-with-extra-anchor)

# 4 - Custom App
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
## 1. Custom App
- Next.js 는 기본으로 제공되는 **`App` 컴포넌트를 사용하여 page를 초기화**한다.
  - `App` 은 `pages` 에 있는 모든 page에 가기 전에 무조건 거쳐가야 하는 길이다.
  - `App` 컴포넌트를 오버라이드하여 페이지 초기화 과정을 커스터마이징할 수 있다.
    - 추가 데이터를 삽입하여 모든 페이지에 공통 속성 적용
    - Global(전역) Styles 추가 ( `<style jsx global></style>` )

- **기본 `App` 을 커스터마이징하고 싶다면 `./pages/_app.js` 파일을 작성**함으로써, `App` 을 오버라이딩 하면 된다.

```
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```    

- ⚠️ 모든 css 파일들(=global css)은 _app.js 파일에서만 import해와서 사용해야 한다. (글로벌 css간의 충돌을 피하기 위해)
  https://nextjs.org/docs/messages/css-global

## 참고
[app.js의 모든 것](https://jake-seo-dev.tistory.com/139)

# #5 - Patterns, Fetching Data
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
## 1. Patterns
- **Layout**
  - React 모델을 사용하면 페이지를 일련의 컴포넌트로 분해할 수 있고, **이러한 컴포넌트 중 다수는 종종 페이지 간에 재사용**된다. <br>(ex. 모든 페이지에 동일한 NavBar, footer)
  - https://nextjs.org/docs/basic-features/layouts
```
import Navbar from './navbar'
import Footer from './footer'
 
export default function Layout({ children }) {
  return (
    <>
      <Navbar />
      <div>{children}</div>
      <Footer />
    </>
  )
}
```

- **Head**
  - **페이지의 `head` 에 요소를 추가**하기 위해 내장 컴포넌트를 노출한다.
  - https://nextjs.org/docs/api-reference/next/head
```
import Head from "next/head";

export default function Seo({ title }) {
  return (
    <Head>
      <title>{title} | Next Movies</title>
    </Head>
  );
}
```


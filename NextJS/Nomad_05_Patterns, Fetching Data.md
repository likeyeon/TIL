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

## 2. Fetching Data
- **async, await**
```
const [movies, setMovies] = useState([]);
  useEffect(() => {
    (async () => {
      const { results } = await (
        await fetch(
          `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`
        )
      ).json();
      setMovies(results);
    })();
  }, []);
```

🤔 **`useEffect` 안에 `async-await`을 사용하는 이유**
1. 처음에 `useEffect` 가 실행될 때 API로부터 데이터를 받아오기 전에 렌더링이 완료되어, loading... 메시지만 표시
2. 즉시 실행 함수(()())로 `await fetch(...)` 를 사용하여, `fetch` 함수가 실행되면 데이터가 반환될 때까지 기다렸다가 결과를 처리할 수 있도록 함

<img width="602" alt="nomad 답변" src="https://github.com/likeyeon/TIL/assets/94125863/80335527-fd25-48e2-a5f6-262e447e30c8">

# #7 - Server Side Rendering 
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
<br/>
- **Server Side Rendering**
  - `SSR`은 서버 사이드 렌더링이라는 뜻으로, **구동 방식은 서버에서 렌더링하여 완성된 HTML 파일을 로드해 준다.**
  - 만약 API load가 느리다면 유저는 아무것도 보지 못한 채 오래 기다려야 한다는 단점이 있음

- **getServerSideProps**
  - 만약 page에서 서버 사이드 랜더링 함수인 `getServerSideProps` 를 export하는 경우, <br/>
    NextJS는 `getServerSideProps` 함수로부터 반환된 데이터를 사용하여 각 request에서 이 페이지를 pre-render할 것이다.
  - `getServerSideProps` 함수는 서버 측에서만 실행되며 브라우저에서는 실행되지 않는다.
    
- `getServerSideProps` 를 사용하여 request 시 데이터 fetch하기
```
export default function Home({ data }) {
// 데이터 랜더링
}

// 매 request마다 실행됨
export async function getServerSideProps() {
  const res = await fetch(`https://.../data`);
  const data = await res.json();
  
  // props를 통해 page에 data전달
  return { props: { data } }
}
```


# #8 - Dynamic Routes, router.push
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
<br/>
## 1. Dynamic Routes
- **동일 pathname 라우팅**
  - routing은 기본적으로 파일명으로 자동 매핑되지만, **동일 pathname 하위의 라우팅을 설정하고 싶다면 pathname으로 폴더를 생성**
  - ex) /movies, /movies/all -> movies 폴더를 생성하고 그 안에 index.js와 all.js 넣기
    
- url에 변수를 넣고 싶다면?
  - ex) /movies/1 -> movies 폴더를 생성하고 그 안에 **[id].js 파일 생성**
 
## 2. Movie Detail
- **router.push(url, as, options)**
  
  - 클라이언트 측 전환을 처리. 이 방법은 next/link가 충분하지 않은 경우에 유용
  - url: UrlObject | String: 탐색할 URL
  - as: UrlObject | String: 브라우저 URL 표시줄에 표시될 경로에 대한 선택적 데코레이터
  - router.push외부 URL에는 사용할 필요없음. window.location의 경우에 사용하는 것이 더 적합.
```
const onClick = (id, title) => {
  router.push(
    {
      pathname: `/movies/${id}`,
      query: {
        title,
      },
    },
    `/movies/${id}`
  );
};
```

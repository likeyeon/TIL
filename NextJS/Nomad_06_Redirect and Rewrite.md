# #6 - Redirect and Rewrite.
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
<br/>
- **API Key 숨기기**
  - 숨기는 이유? API Key의 사용량이 제한되어있는데 공개된 경우, 다른 사람들이 남용할 수도 있기 때문
  - inspect -> network에 들어가면 url안에 api key가 노출되어 있음
  - `rewrite` 를 사용하여 api key를 mask 처리하여 숨길 수 있음

- **redirect와 rewrite**
  - 공통점 : 유저가 특정 path로 이동 시 정해진 다른 대상 경로로 리디렉션
  - 차이점 :
    - **`redirect` 는 정해진 path로 url이 바뀌는** 반면
    - **`rewrite` 는 유저가 입력한 url이 유저에게 그대로 보여져** url 변화를 볼 수 없음

- **관련 속성**
  - `source` : 들어오는 요청 경로 패턴
  - `destination` : 라우팅하려는 경로
  - `permanent`
      - `true` 또는 `false`
      - 영구적인지/아닌지에 따라 브라우저나 검색엔진이 정보를 기억하는지 여부가 결정됨.
  - `:path` : `:`를 이용해 다이나믹한 path 값을 받아올 수 있음
  - path 옆에 `*` 을 붙이면, 경로 길이 상관없이 무엇이든 올 수 있음을 의미

```
/* next.config.js */

const API_KEY = process.env.API_KEY; // .env 파일에 API_KEY 변수를 생성하여 값을 할당하고 필요할 때마다 꺼내 씀

const nextConfig = {
  reactStrictMode: true,
  async redirects() {
    return [
      {
        source: "/old-blog/:path*",
        destination: "/new-sexy-blog/:path*",
        permanent: false,
      },
    ];
  },
  async rewrites() {
    return [
      {
        source: "/api/movies",
        destination: `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`,
      },
    ];
  },
};
```
 
## 참고
- https://nextjs.org/docs/app/api-reference/next-config-js/redirects <br/>
- [next.js의 rewrite와 redirect](https://velog.io/@deli-ght/nextrewrite%EC%99%80-redirect)

# #8 - Catch All, 404 Pages
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
<br/>
## 1. Catch All
- catch all
  - 점 세개를 사용해서 모든 path를 잡을 수 있음
  - ex) pages/movies/[...params] 파일 -> `/movies/a/bc/def` 가능
    
❗️ NextJS 13 업데이트 이후로, getServerSideProps 사용 X. 대신 아래로 사용
- getStaticProps
  - 페이지에서 getStaticProps(정적 사이트 생성)이라는 함수를 내보내면 Next.js는 getStaticProps에서 반환된 props를 사용하여 빌드 시 이 페이지를 pre-rendering 한다.

- getStaticPaths
  - 페이지에 동적 경로가 있고 getStaticProps를 사용하는 경우 정적으로 생성할 경로 목록을 정의해야 한다.
  - 동적 경로를 사용하는 페이지에서 getStaticPaths(정적 사이트 생성)이라는 함수를 내보낼 때 Next.js는 getStaticPaths에서 지정한 모든 경로를 정적으로 pre-rendering 한다.
 
## 2. 404 Pages
- pages폴더 밑에 404.js 파일 생성
<br/>
 
### 참고
[nextjs에서 params 및 router](https://imported-sturgeon-51f.notion.site/nextjs-params-router-d7e6c04fdd094adc90418c269af107fd)


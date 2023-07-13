# 1. Start, Library VS Framework
본 내용은 [Nomad Coders - NextJS 시작하기 강의](https://nomadcoders.co/nextjs-fundamentals)를 토대로 작성하였습니다.
## 1. Start

### 설치

`npx create-next-app@latest`

### 실행

`npm run dev`

## 2. library VS framework

- 라이브러리
  - 사용자가 파일 이름이나 구조 등을 정하고, 모든 결정을 내림
  - 사용자가 적절히 가져다가 씀
  - ex. React.js
- 프레임워크
  - 파일 이름이나 구조 등을 정해진 규칙에 따라 만들고 따름
  - 정해진 틀 안에서 커스터마이징
  - ex. Next.js
- 자유도의 차이
  - 라이브러리 > 프레임워크
- Inversion of Control (통제의 역전)
  - 라이브러리에서 메서드를 호출하면 사용자가 제어할 수 있다.
  - 프레임워크에서는 제어가 역전되어 프레임워크가 사용자를 호출한다.

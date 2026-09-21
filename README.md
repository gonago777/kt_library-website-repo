# KT Library Website

도서 등록·조회·관리 기능과 사용자 상호작용 기능을 제공하는 React 기반 웹 클라이언트입니다.

> 이 저장소에는 **프론트엔드 코드**가 포함되어 있으며, REST API 서버는 기본적으로 `http://localhost:8080`을 사용하도록 구성되어 있습니다.

## 주요 기능

- 회원가입 / 로그인 / 로그아웃
- 세션 상태 확인
- 도서 목록 및 상세 조회
- 도서 등록 / 수정 / 삭제
- 내 도서 목록 조회
- 댓글 작성 / 조회 / 삭제
- 좋아요 및 찜 기능
- 도서 검색
- AI 표지 생성 API 호출 및 생성 이미지 URL 저장

## Tech Stack

- **Frontend:** React 19, JavaScript
- **Build Tool:** Vite 7
- **Routing:** React Router
- **HTTP Client:** Axios
- **UI:** MUI, Emotion
- **Build:** Node.js 20, AWS CodeBuild `buildspec.yml`

## API 연동

프론트엔드 서비스 모듈에서 백엔드 REST API를 호출합니다.

### Authentication
- `POST /users/signup`
- `POST /users/login`
- `POST /users/logout`
- `GET /users/session-check`

### Books
- `GET /books`
- `GET /books/{id}`
- `POST /books`
- `PUT /books/{id}`
- `DELETE /books/{id}`
- `GET /books/my`

### AI Cover
- `POST /books/ai-cover`
- `PUT /books/ai-image`

### Comments / Favorites / Likes
- 댓글 조회·작성·삭제
- 찜 추가·해제 및 상태 조회
- 좋아요 추가·해제 및 상태 조회

## 실행 방법

Node.js가 설치된 환경에서 다음 명령을 실행합니다.

```bash
npm install
npm run dev
```

Vite 개발 서버가 실행된 뒤, 백엔드 API 서버가 `http://localhost:8080`에서 실행 중이어야 주요 기능을 사용할 수 있습니다.

## Build

```bash
npm run build
```

`buildspec.yml`은 Node.js 20 환경에서 의존성을 설치하고 Vite 빌드를 수행한 뒤 `dist` 디렉터리를 산출물로 생성하도록 구성되어 있습니다.

## Repository Structure

```text
src/
├─ components/   # 공통 UI 컴포넌트
├─ pages/        # 화면 단위 컴포넌트
└─ services/     # 백엔드 API 연동 모듈
```

## 구현 포인트

- Axios의 `withCredentials`를 사용한 세션 기반 요청 처리
- React Router를 이용한 도서 상세·수정 페이지 라우팅
- API 호출 로직을 `services` 영역으로 분리
- 도서 CRUD와 사용자 상호작용 기능을 REST API와 연결

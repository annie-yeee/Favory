# Favory 🎵🎬📚

> Open API 기반 음악·영화·드라마·도서 통합 문화생활 기록 및 공유 플랫폼

우리는 누군가를 만날 때 흔히 서로의 취향을 묻지만, 정작 내 취향을 정리해 본 적은 많지 않습니다. 좋아하는 콘텐츠를 한눈에 모아보고, 나만의 취향을 기록할 수 있는 공간을 만들고자 한 프로젝트에 참여하게 되었습니다.

---

## 🛠 기술 스택
| 분류 | 기술 |
|------|------|
| Language | Kotlin 1.9 |
| Runtime | Java 21 |
| Framework | Spring Boot 3, JPA |
| Database | MySQL |
| Infra | AWS EC2 |
| Docs | Swagger |
| Test | JMeter |
| Auth | JWT, Google OAuth |

---

## 👥 팀 구성
| 역할 | 담당 |
|------|------|
| Frontend | 기획/디자인/프론트엔드 개발 |
| Backend | Open API 연동, 감상평 CRUD, 이메일 인증 |
| Backend (본인) | 인증/로그인, 검색, 좋아요, 성능 개선, 배포 |

---

## 담당 기능 (김우영)

### 🤝 API 협업
- 프론트엔드 요구사항 기반으로 Swagger API 명세 협의 및 작성
- 응답 스펙 변경 시 Swagger 문서 우선 업데이트 후 공유

### 👤 프로필
- 닉네임 정규화 및 자동 생성
- 닉네임 기반 프로필 조회 API

### 🔐 인증 / 로그인
- 로그인·회원가입 API 구현 및 인증 흐름 설계
- JWT 기반 Access/Refresh Token 발급 처리
- Refresh Token 갱신 처리
- Google OAuth 간편 로그인 구현
- GlobalExceptionHandler 프로젝트 최초 도입
    (흩어진 예외처리를 공통 로직으로 분리해 일관된 에러 응답 구조 확립)
- 이메일/닉네임 중복 검사 예외 처리

### 🔍 검색
- 검색 API 설계 및 최근 검색어 저장·삭제 기능 구현
- 태그 검색 시 mediaType 필터링

### 👍 좋아요 / 정렬
- 좋아요 기능 구현
- 인기순 정렬 기능 구현

### ⚡ 성능 개선
사용자 피드백에서 "전체적으로 데이터 가져오는 데 시간이 오래 소요됨" 의견을 받아 JMeter로 원인을 진단했습니다.
JPA N+1 문제가 원인이었고, Fetch Join + 태그 리스트 일괄 조회를 적용해 개선했습니다.

| 지표 | AS-IS | TO-BE | 개선율 |
|------|-------|-------|--------|
| SQL 호출 수 | 12회 | 3회 | 75% 감소 |
| 평균 응답속도 | 155ms | 96ms | 38% 단축 |
| TPS | 6.4/sec | 10.2/sec | 59% 향상 |

**AS-IS (개선 전)**
<img width="1133" height="223" alt="jmeter-before" src="https://github.com/user-attachments/assets/d657aa1b-8f64-4d68-ae81-5c30fd7247e9" />


**TO-BE (개선 후)**
<img width="1132" height="228" alt="jmeter-after" src="https://github.com/user-attachments/assets/0a807da5-b6e0-4240-b319-7770fd912ab8" />

### 🚀 인프라 / 배포
- AWS EC2 서버 배포 및 운영
- Docker Compose 기반 배포 환경 구성 및 환경변수 관리
- ERD 설계 참여

---

## 📅 프로젝트 기간
2025.10 ~ 2026.03 (5개월)

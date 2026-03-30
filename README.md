
<div align="center">

![logo](https://github.com/user-attachments/assets/5e42c354-6b87-4eca-b0cb-518bc5fd1ce1)

**Flutter + Spring Boot 기반 AI 여행 메모 서비스**

여행 기록을 단순 저장하는 것을 넘어, 메모 작성부터 폴더 관리, AI 요약/번역/캡션 추천, 장소 추출 및 지도 시각화, 일정 확인까지 지원하는 모바일 중심 프로젝트입니다.

[![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?logo=flutter&logoColor=white)](https://flutter.dev/)
[![Dart](https://img.shields.io/badge/Dart-3.6.1-0175C2?logo=dart&logoColor=white)](https://dart.dev/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)

**진행 형태:** Flutter 프론트엔드 + Spring Boot 백엔드 통합 프로젝트

</div>

<br><br>

## 📋 목차

- [프로젝트 소개](#-프로젝트-소개)
- [주요 기능](#-주요-기능)
- [기술 스택](#-기술-스택)
- [프로젝트 구조](#-프로젝트-구조)
- [아키텍처 및 설계 전략](#-아키텍처-및-설계-전략)
- [시작하기](#-시작하기)
- [팀원](#-팀원)

<br><br>

## 🎯 프로젝트 소개

### 프로젝트 목표

- ✅ 여행 메모를 폴더 단위로 체계적으로 관리할 수 있는 구조 설계
- ✅ 로그인, 회원가입, 비밀번호 재설정 등 사용자 인증 플로우 구현
- ✅ AI 기반 요약, 번역, 장소 추출, 캡션 추천 기능 통합
- ✅ 메모와 여행지 정보를 연결한 지도 기반 시각화 제공
- ✅ 온라인/오프라인 사용 흐름을 고려한 사용자 경험 구성

<br><br>

## ✨ Functions

### 🔐 로그인 / 회원가입

#### 인증 플로우
- 이메일 / 비밀번호 기반 로그인
- 단계형 회원가입 화면 구성
- 비밀번호 찾기 및 재설정 기능
- JWT 토큰 저장 기반 인증 처리

### 부가 기능
- 로그인 없이 사용하는 오프라인 진입 지원
- 구글 / 카카오 소셜 로그인 화면 분리 구성
- 입력값 검증 및 예외 상황 안내

<br>

### 📁 여행 폴더 관리

#### 폴더 생성 및 편집
- 여행 이름, 지역, 일정, 목적 기반 폴더 생성
- 폴더명 수정
- 폴더 색상 변경
- 대표 이미지 설정

#### 사용자 액션
- 즐겨찾기 토글
- 폴더 삭제
- 검색 기반 폴더 탐색
- 여행 목적별 메모 분류 기반 관리

<br>

### 📝 메모 작성 / 편집

#### 에디터 기능
- 제목 + 본문 기반 메모 작성
- `flutter_quill` 기반 리치 텍스트 편집
- 이미지 삽입 지원
- Undo / Redo 지원
- 날짜 선택 기반 메모 작성 시점 관리

#### 저장 흐름
```text
일반 메모 작성 → 폴더에 저장
퀵 메모 작성 → 빠른 저장 API 호출
기존 메모 진입 → 수정 후 업데이트
```

<br>

### 🤖 AI 메모 보조
<br>
<img width="6082" height="2424" alt="448869362-9bca308b-cdf9-4faf-a42e-cb916f034adb" src="https://github.com/user-attachments/assets/37a0f57e-5ba8-4a2f-9d81-1b7915de717d" />


#### AI 모달 시트
- 메모 화면에서 플로팅 버튼으로 AI 기능 호출
- 탭 기반 AI 결과 탐색
- 메모 내용 변경 시 재요청 가능

#### 제공 기능
- **요약:** 메모 핵심 내용 자동 요약 <br>
<img width="2323" height="2424" alt="448869771-93d582ef-e99c-4a63-b12e-abcd82f611f9" src="https://github.com/user-attachments/assets/4ae04f8d-9081-47d0-a179-91f37c5e85fb" />

- **번역:** 메모 자동 번역 및 본문 대체 <br>
<img width="4597" height="2429" alt="448870137-e0fe9080-9eb1-43d8-8e2a-93ffbe8d931a" src="https://github.com/user-attachments/assets/9dbb0567-438e-4f63-b068-e15b7e53e121" />

- **장소 추출:** 메모 속 장소명 분석 <br>
<img width="251" height="528" alt="448870373-ae6bfcd0-3cf1-40ec-b9b8-c2a6f8dc6b85" src="https://github.com/user-attachments/assets/dd1ca0bc-73ca-46db-b3aa-f0ee2974cc06" />

- **캡션 추천:** 여행 메모용 짧은 문구 / 해시태그 생성 <br>
<img width="250" height="528" alt="448870664-b0c640d5-40a8-4636-a72c-9087d59d53f4" src="https://github.com/user-attachments/assets/c56a7333-11ff-4029-9704-320f631c2db4" />


#### 활용 흐름
```text
메모 작성 → AI 버튼 클릭 → 기능 탭 선택
  ├─ 요약: 핵심 문장 확인
  ├─ 번역: 결과 확인 후 본문 대체
  ├─ 장소: 추출 장소를 지도에 표시
  └─ 캡션: SNS용 문구 추천
```

<br>

### 🗺️ 지도 기반 장소 확인

#### 지도 연동
- 메모 본문에서 장소명 추출
- 번역 및 지오코딩 후 좌표 변환
- Google Maps 기반 마커 시각화
- 장소 목록 클릭 시 해당 위치로 이동

#### 사용자 가치
- 텍스트 메모를 지도 정보로 확장
- 여행 동선 파악 보조
- 여행지 후보를 직관적으로 확인 가능

<br>

### 📅 캘린더 기반 메모 확인

#### 일정 확인 기능
- 월간 캘린더 UI 제공
- 선택한 날짜의 메모 목록 조회
- 메모 수정일 기준 일자별 확인
- 스크롤 가능한 카드형 리스트 제공

#### 사용 시나리오
- 특정 날짜에 작성한 여행 메모 회고
- 일정별 기록 탐색
- 캘린더 중심 기록 관리

<br>

### ⚙️ 사이드바 / 부가 화면

#### 사이드 메뉴
- 프로필 카드 표시
- 즐겨찾기 화면 이동
- 설정 화면 이동
- 공유 / 친구 / 휴지통 등 확장 메뉴 구조 반영

#### 설정 영역
- 디스플레이 설정
- 언어 설정
- 알림 설정
- 보안 설정
- AI 관련 설정 화면 분리

<br><br>

## 🛠 기술 스택

### Core
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)

### UI & Styling
![Material UI](https://img.shields.io/badge/Material_UI-1976D2?style=for-the-badge&logo=materialdesign&logoColor=white)
![Flutter Quill](https://img.shields.io/badge/Flutter_Quill-4A4A4A?style=for-the-badge&logo=flutter&logoColor=white)
![Montserrat](https://img.shields.io/badge/Font-Montserrat-222222?style=for-the-badge)

### State & Storage
![Provider](https://img.shields.io/badge/Provider-2196F3?style=for-the-badge)
![Shared Preferences](https://img.shields.io/badge/Shared_Preferences-FF9800?style=for-the-badge)

### Networking & API
![HTTP](https://img.shields.io/badge/HTTP-5C6BC0?style=for-the-badge)
![REST API](https://img.shields.io/badge/REST_API-009688?style=for-the-badge)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)

### AI & External Services
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Google Maps](https://img.shields.io/badge/Google_Maps-4285F4?style=for-the-badge&logo=googlemaps&logoColor=white)
![Google Translate](https://img.shields.io/badge/Translate_API-34A853?style=for-the-badge&logo=googletranslate&logoColor=white)

### Code Quality
![Flutter Lints](https://img.shields.io/badge/Flutter_Lints-46B2F0?style=for-the-badge)
![Build Runner](https://img.shields.io/badge/Build_Runner-6E9F18?style=for-the-badge)

<details>
<summary><b>상세 버전</b></summary>

| Category | Stack |
|----------|-------|
| Language | Dart 3.6.1, Java |
| Framework | Flutter, Spring Boot |
| UI Editor | flutter_quill |
| State Management | Provider |
| Local Storage | SharedPreferences |
| Networking | http |
| Maps | google_maps_flutter, Google Geocoding API |
| Utility | intl, image_picker, permission_handler |
| Auth | Spring Security, JWT |
| AI/Analysis | OpenAI API, Translation Service |
| Testing | flutter_test |
| Code Quality | flutter_lints, build_runner |
| Package Manager | pub |
| Runtime | Android, iOS, Web, Desktop |

</details>
<br><br>

<img width="3588" height="1892" alt="448868135-3144e8d0-41ce-4f1e-a9d6-8e1bb48ee438" src="https://github.com/user-attachments/assets/dc02f524-916d-443b-8fbf-078743cf03a1" />


<br><br>

## 📁 프로젝트 구조


```text
memoRE/
├── lib/
│   ├── presentation/                 # 📱 온라인 메인 앱 화면
│   │   ├── screen/auth/             # 로그인, 회원가입, 비밀번호 재설정
│   │   ├── screen/home/             # 홈, 폴더, 메모, 캘린더
│   │   └── screen/sidebar/          # 프로필, 설정, 즐겨찾기, 친구
│   ├── offline/                      # 📴 오프라인 전용 화면 구성
│   └── main.dart                     # 앱 진입점
├── assets/
│   ├── fonts/                        # 폰트 리소스
│   ├── icons/                        # 아이콘 리소스
│   └── images/                       # 이미지 리소스
├── backend/
│   └── src/main/java/com/example/demo/
│       ├── controller/               # REST API 컨트롤러
│       ├── service/                  # 비즈니스 로직
│       ├── repository/               # 데이터 접근 계층
│       ├── model/                    # 엔티티 / 모델
│       ├── dto/                      # 요청 / 응답 DTO
│       ├── security/                 # JWT 필터, 보안 설정
│       └── config/                   # Spring 설정
├── android/                          # Android 플랫폼 설정
├── ios/                              # iOS 플랫폼 설정
├── web/                              # Web 설정
├── macos/                            # macOS 설정
├── windows/                          # Windows 설정
├── linux/                            # Linux 설정
└── README.md
```

<br><br>

## 🏗️ 아키텍처 및 설계 전략

### 1️⃣ Flutter 프론트엔드 + Spring Boot 백엔드 분리

#### 📦 역할 분리
```text
Flutter
- 사용자 화면 구성
- 메모 작성/편집 UX 제공
- 지도/캘린더/드로어 등 인터랙션 처리

Spring Boot
- 인증 / 인가 처리
- 메모 / 폴더 / 친구 API 제공
- AI / 번역 / 지도 분석 로직 통합
```

**효과:**
- ✅ UI와 비즈니스 로직의 책임 분리
- ✅ 기능 확장 시 유지보수성 향상
- ✅ 모바일 앱과 서버의 독립적인 개발 가능

<br>

### 2️⃣ JWT 기반 인증 구조

#### 🔐 인증 처리
```java
- /login 으로 인증 수행
- 토큰 발급 후 클라이언트 저장
- 요청 시 Authorization 헤더 기반 인증
- Spring Security + JwtFilter 조합 적용
```

**설계 의도:**
- 🔄 세션 의존도를 낮춘 인증 구조
- 🔒 보호된 API에 대한 일관된 접근 제어
- 👤 사용자별 메모 / 폴더 데이터 분리

<br>

### 3️⃣ 폴더 중심 메모 구조 설계

#### 🗂️ 데이터 흐름
```text
폴더 생성 → 여행 단위 메모 분류
메모 저장 → 폴더별 목록 조회
퀵 메모 저장 → 별도 빠른 기록 흐름 제공
캘린더 조회 → 날짜 기준 전체 메모 확인
```

**효과:**
- ✅ 여행별 기록 정리 용이
- ✅ 메모 탐색성과 회고 효율 향상
- ✅ 일반 메모와 퀵 메모 사용 패턴 분리

<br>

### 4️⃣ AI 기능을 모달 시트로 통합

#### 🤖 탭형 AI 인터페이스
```text
요약 / 번역 / 장소 / 캡션 기능을
하나의 모달 시트 안에서 탭으로 제공
```

**설계 목적:**
- ✅ 메모 작성 흐름을 끊지 않고 AI 기능 호출
- ✅ 기능별 결과를 동일한 진입점에서 확인
- ✅ 번역 결과를 본문에 바로 반영하는 연결 구조 확보

<br>

### 5️⃣ 장소 추출 + 지도 시각화 파이프라인

#### 🗺️ 처리 흐름
```text
메모 텍스트
→ OpenAI 기반 장소 추출
→ 번역 서비스로 영문 변환
→ Geocoding API로 좌표 변환
→ Google Map 마커 렌더링
```

**효과:**
- 📍 비정형 메모를 위치 정보로 변환
- 🧭 여행 기록의 시각적 이해도 향상
- 🔎 장소 기반 탐색 경험 제공

<br>

### 6️⃣ 온라인 / 오프라인 분리 화면 구성

#### 📴 사용 환경 대응
```text
presentation/  : 서버 연동 중심 화면
offline/       : 비로그인 / 로컬 중심 화면
```

**효과:**
- ✅ 네트워크 상황과 로그인 여부에 따른 대응 가능
- ✅ 서비스 확장 전 실험용 UI와 운영 UI 분리
- ✅ 사용자 진입 장벽 완화

<br><br>

## 🚀 시작하기

### 요구사항
- Flutter SDK 3.x 이상
- Dart SDK 3.6.1 이상
- JDK 17 이상
- Android Studio 또는 VS Code
- Spring Boot 실행 환경

### 설치 및 실행
```bash
# 1. 저장소 클론
git clone https://github.com/your-username/memoRE.git

# 2. Flutter 의존성 설치
cd memoRE
flutter pub get

# 3. Flutter 앱 실행
flutter run

# 4. 백엔드 서버 실행
# backend 프로젝트를 IDE(IntelliJ 등)에서 실행하거나
# Spring Boot 실행 환경에 맞게 서버 기동
```

### 환경 변수 / 설정
```env
# Flutter / Backend 실행 시 사용되는 주요 설정 예시
OPENAI_API_KEY=your_openai_api_key
GOOGLE_MAPS_API_KEY=your_google_maps_api_key
BASE_URL=http://localhost:8080
```

<br><br>

## 👥 팀원

| Name | Role | GitHub |
|------|------|--------|
| 이다민 | 서버 개발, API 구축, AI 기능 연동, 배포 및 운영 | [@dadadadamin](https://github.com/dadadadamin) |
| 박규나 | PM, UI/UX 디자인, Flutter UI/UX 개발 | [@qnada0118](https://github.com/qnada0118) |
| 백준호 | 서버 아키텍처 설계, API 구현, 데이터 처리, 보안 및 DB 관리 | [@JUNHO0712](https://github.com/JUNHO0712) |
| 송정원 | Flutter UI/UX 개발, 서버 연동, 기능 테스트 | [@alvn84](https://github.com/alvn84) |
| 차재혁 | UI/UX 디자인, 세부 화면 설계 및 개발 | [@jhcha329](https://github.com/jhcha329) |


<br><br>
<div align="center">

[⬆️ Back to top](#-memore)

</div>

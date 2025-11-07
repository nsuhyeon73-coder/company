[README.md](https://github.com/user-attachments/files/23411828/README.md)
# Company Portal 🏢

PHP 기반의 기업 포털 웹 애플리케이션입니다. 직장인, 취준생, 학생들을 위한 커뮤니티 플랫폼을 제공합니다.

## 📋 주요 기능

- **사용자 인증 시스템**: 회원가입, 로그인, 세션 관리
- **게시판 시스템**: 익명 게시판, 스터디 게시판, 공지사항
- **채용 정보**: 채용 공고 조회 및 상세 정보
- **취준생 지원**: 취업 준비를 위한 리소스 및 정보
- **마이페이지**: 사용자 프로필 및 활동 관리
- **반응형 디자인**: 모바일, 태블릿, 데스크톱 지원

## 🛠️ 기술 스택

- **Backend**: PHP 7.4+
- **Database**: MySQL 5.7+ / MariaDB
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Libraries**: 
  - MySQLi (Database)
  - Session Management
  - Password Hashing (PHP built-in)

## 📦 설치 방법

### 1. 사전 요구사항

- PHP 7.4 이상
- MySQL 5.7 이상 또는 MariaDB
- Apache/Nginx 웹 서버
- XAMPP, WAMP, MAMP 등의 로컬 개발 환경 (선택사항)

### 2. 프로젝트 클론

```bash
git clone https://github.com/yourusername/company-portal.git
cd company-portal
```

### 3. 데이터베이스 설정

1. `db.php` 파일에서 데이터베이스 연결 정보 수정:

```php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');
define('DB_PASS', '');
define('DB_NAME', 'company_portal');
```

2. 브라우저에서 `install.php` 접속하여 자동 설치:

```
http://localhost/company-portal/install.php
```

### 4. 관리자 계정

설치 후 기본 관리자 계정:
- **이메일**: admin@company.com
- **비밀번호**: admin123

> ⚠️ **보안 경고**: 첫 로그인 후 반드시 비밀번호를 변경하세요!

## 📁 프로젝트 구조

```
company-portal/
├── index.php           # 메인 페이지
├── login.php           # 로그인 페이지
├── logout.php          # 로그아웃 처리
├── board.php           # 익명 게시판
├── study.php           # 스터디 게시판
├── jobs.php            # 채용 정보 목록
├── job_detail.php      # 채용 상세 정보
├── jobseeker.php       # 취준생 페이지
├── notice.php          # 공지사항
├── mypage.php          # 마이페이지
├── install.php         # 설치 스크립트
├── db.php              # 데이터베이스 연결 및 유틸리티
├── style.css           # 메인 스타일시트
├── script.js           # JavaScript 기능
└── README.md           # 프로젝트 문서
```

## 🗄️ 데이터베이스 스키마

### users 테이블
```sql
- id (INT, PRIMARY KEY, AUTO_INCREMENT)
- username (VARCHAR(50))
- email (VARCHAR(100), UNIQUE)
- password (VARCHAR(255))
- user_type (ENUM: '직장인', '취준생', '학생', '관리자')
- created_at (TIMESTAMP)
```

### posts 테이블
```sql
- id (INT, PRIMARY KEY, AUTO_INCREMENT)
- user_id (INT, FOREIGN KEY)
- title (VARCHAR(200))
- content (TEXT)
- category (VARCHAR(50))
- views (INT)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)
```

### comments 테이블
```sql
- id (INT, PRIMARY KEY, AUTO_INCREMENT)
- post_id (INT, FOREIGN KEY)
- user_id (INT, FOREIGN KEY)
- content (TEXT)
- created_at (TIMESTAMP)
```

### likes 테이블
```sql
- id (INT, PRIMARY KEY, AUTO_INCREMENT)
- post_id (INT, FOREIGN KEY)
- user_id (INT, FOREIGN KEY)
- created_at (TIMESTAMP)
- UNIQUE(post_id, user_id)
```

## 🚀 주요 기능 설명

### 1. 메인 페이지 (index.php)
- 배너 슬라이더
- 실시간 검색 기능
- 최신 스터디, 공지사항, 게시판 글 표시
- 실시간 시계 및 달력

### 2. 게시판 시스템
- 익명 게시판: 자유로운 의견 공유
- 스터디 게시판: 학습 자료 및 스터디 모집
- 카테고리별 게시글 분류
- 조회수, 댓글, 좋아요 기능

### 3. 채용 정보
- 채용 공고 목록 조회
- 상세 정보 보기
- 지역 및 경력별 필터링

### 4. 사용자 관리
- 회원가입 및 로그인
- 사용자 타입별 권한 관리
- 마이페이지에서 프로필 관리

## 🔒 보안 기능

- **XSS 방지**: `htmlspecialchars()` 함수로 입력값 정제
- **SQL Injection 방지**: Prepared Statements 사용
- **비밀번호 암호화**: `password_hash()` 사용
- **세션 관리**: 안전한 세션 처리
- **입력값 검증**: 서버사이드 유효성 검사

## 🎨 UI/UX 특징

- **반응형 디자인**: 모든 디바이스에서 최적화된 경험
- **모던한 그라데이션**: 보라색 계열의 세련된 디자인
- **직관적인 네비게이션**: 햄버거 메뉴 및 드롭다운
- **부드러운 애니메이션**: CSS transition 효과
- **접근성 고려**: 시맨틱 HTML 및 명확한 UI

## 🐛 알려진 이슈

- 파일 업로드 기능 미구현
- 이메일 알림 기능 미구현
- 관리자 페이지 추가 개발 필요

## 🔄 향후 개발 계획

- [ ] 파일 첨부 기능
- [ ] 이메일 인증 시스템
- [ ] 관리자 대시보드
- [ ] 실시간 알림 기능
- [ ] API 연동
- [ ] PWA 지원

## 📝 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다.

## 👥 기여하기

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📧 문의

프로젝트에 대한 문의사항이 있으시면 이슈를 등록해주세요.

## 🙏 감사의 말

이 프로젝트를 사용해주셔서 감사합니다!

---

⭐️ 이 프로젝트가 도움이 되셨다면 Star를 눌러주세요!

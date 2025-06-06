# Survey Backend API

FastAPI 기반의 설문조사 백엔드 API 서버입니다.

## 기능

- 사용자 인증 (JWT)
- 워크스페이스 관리
- 설문 생성 및 관리
- 엑셀 파일 업로드를 통한 설문 문항 생성
- 학생용 설문 평가 시스템
- 대시보드 및 통계
- 리포트 생성 및 S3 저장

## 설치 및 실행

### 1. 의존성 설치

```bash
pip install -r requirements.txt
```

### 2. 환경 변수 설정

`.env` 파일을 생성하고 다음 내용을 설정합니다:

```env
# Database
DATABASE_URL=mysql+pymysql://root:password@localhost/survey_db

# JWT
SECRET_KEY=your-secret-key-here-change-this-in-production

# AWS S3
AWS_ACCESS_KEY_ID=your-aws-access-key
AWS_SECRET_ACCESS_KEY=your-aws-secret-key
AWS_REGION=ap-northeast-2
S3_BUCKET_NAME=survey-uploads
```

### 3. 데이터베이스 테이블 생성

```bash
python create_tables.py
```

### 4. 서버 실행

```bash
python main.py
```

또는

```bash
uvicorn main:app --host 0.0.0.0 --port 8080 --reload
```

## API 문서

서버 실행 후 다음 URL에서 API 문서를 확인할 수 있습니다:

- Swagger UI: http://localhost:8080/docs
- ReDoc: http://localhost:8080/redoc

## 프로젝트 구조

```
.
├── main.py                 # FastAPI 애플리케이션 진입점
├── database/              # 데이터베이스 연결 설정
│   └── connection.py
├── models/                # SQLAlchemy 모델
│   ├── __init__.py
│   ├── user.py
│   ├── workspace.py
│   └── survey.py
├── schemas/               # Pydantic 스키마
│   ├── auth.py
│   ├── workspace.py
│   └── survey.py
├── routers/               # API 라우터
│   ├── __init__.py
│   ├── auth.py
│   ├── workspaces.py
│   ├── surveys.py
│   ├── assessment.py
│   ├── dashboard.py
│   ├── reports.py
│   └── files.py
├── utils/                 # 유틸리티 함수
│   └── auth.py
├── create_tables.py       # DB 테이블 생성 스크립트
├── requirements.txt       # 의존성 목록
└── README.md             # 프로젝트 문서
``` 
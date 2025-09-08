# Claude Code 커스텀 커맨드

TypeScript/NestJS 프로젝트를 위한 Claude Code 커스텀 커맨드 모음입니다. 코드 리뷰, 성능 최적화 분석, PR 설명 자동 생성, 테스트 코드 작성 등의 개발 워크플로우를 자동화합니다.

## 📋 커맨드 목록

### `/optimize` - 성능 최적화 분석
브랜치, PR, 또는 특정 파일의 성능 최적화 분석을 수행합니다.

**사용법:**
```bash
/optimize                    # 현재 브랜치 변경사항 분석
/optimize branch-name        # 특정 브랜치 분석
/optimize 123               # PR 번호로 분석
/optimize 123 --comment     # PR 분석 후 자동 댓글 등록
/optimize src/service.ts    # 특정 파일 분석
```

**분석 항목:**
- 데이터베이스 쿼리 최적화 (N+1 문제, 인덱스)
- 메모리 사용량 및 누수 검사
- 알고리즘 시간 복잡도 개선
- 캐싱 전략 (Redis, 메모리, 응답 캐싱)
- 비동기 처리 및 병렬화
- NestJS/Prisma 특화 최적화

### `/review` - 코드 리뷰
종합적인 코드 리뷰를 통해 품질 개선사항을 제안합니다.

**사용법:**
```bash
/review                     # 현재 브랜치 리뷰
/review branch-name         # 특정 브랜치 리뷰
/review 123                # PR 리뷰
/review 123 --comment      # PR 리뷰 후 자동 댓글 등록
/review src/controller.ts  # 특정 파일 리뷰
```

**리뷰 항목:**
- 코드 품질 (가독성, 유지보수성, 성능)
- 보안 취약점 검토
- TypeScript/NestJS 모범 사례
- 테스트 커버리지 및 테스트 가능성
- 아키텍처 및 의존성 관리
- Prisma 스키마 및 마이그레이션

### `/pr-description` - PR 설명 자동 생성
PR 변경사항을 분석하여 템플릿 기반으로 상세한 설명을 생성합니다.

**사용법:**
```bash
/pr-description             # 현재 브랜치 기반 설명 생성
/pr-description branch-name # 특정 브랜치 기반 생성
/pr-description 123         # PR 분석 후 설명 생성
/pr-description 123 --update # PR 설명 자동 업데이트
```

**생성 내용:**
- 작업 배경 및 관련 히스토리
- 추가/수정/리팩토링 변경사항 분류
- 리뷰 포인트 및 검토 사항
- 적정 리뷰 기한 제안

### `/test` - 테스트 코드 생성
포괄적인 테스트 코드를 Jest와 NestJS Testing Module을 사용하여 생성합니다.

**사용법:**
```bash
/test [파일경로 또는 코드]
```

**테스트 유형:**
- 단위 테스트 (Given-When-Then 형식)
- 통합 테스트 (모듈 간 상호작용)
- 엣지 케이스 (경계값, 예외 상황)
- 모킹 (외부 의존성, HTTP, 서드파티)

## ⚙️ 설정

### Prettier 자동 포맷팅
TypeScript 파일 편집 시 자동으로 Prettier 포맷팅이 적용됩니다.
```json
// hooks/prettier.json
{
  "hooks": {
    "PostToolUse": [...]
  }
}
```

### GitHub CLI 연동
PR 관련 기능 사용을 위해 GitHub CLI가 설치되어 있어야 합니다.
```bash
# GitHub CLI 설치 및 인증
gh auth login
```

## 🚀 사용 예시

### 1. PR 리뷰 자동화
```bash
# PR 리뷰 후 자동 댓글 등록
/review 123 --comment
```

### 2. 성능 최적화 분석
```bash
# 특정 브랜치의 성능 분석
/optimize feature/user-service
```

### 3. PR 설명 자동 생성 및 업데이트
```bash
# PR 설명 자동 생성 후 업데이트
/pr-description 123 --update
```

## 📁 프로젝트 구조

```
├── commands/              # 커스텀 커맨드 정의
│   ├── optimize.md       # 성능 최적화 분석
│   ├── review.md         # 코드 리뷰
│   ├── pr-description.md # PR 설명 생성
│   └── test.md          # 테스트 생성
├── hooks/               # Claude Code 훅 설정
│   └── prettier.json    # Prettier 자동 포맷팅
├── CLAUDE.md           # Claude Code 가이드
└── README.md           # 프로젝트 문서
```

## 🎯 주요 특징

- **한국어 지원**: 모든 분석 결과와 설명은 한국어로 제공
- **TypeScript/NestJS 특화**: TypeScript와 NestJS 프로젝트에 최적화
- **GitHub 워크플로우 통합**: PR 댓글 자동 등록 및 설명 업데이트
- **포괄적 분석**: 성능, 보안, 코드 품질을 종합적으로 검토
- **자동화 중심**: 반복적인 개발 작업을 자동화하여 생산성 향상

## 🔧 요구사항

- Claude Code CLI
- Node.js 프로젝트 (TypeScript/NestJS 권장)
- GitHub CLI (PR 관련 기능 사용 시)
- Prettier (코드 포맷팅)

---

이 커맨드들을 사용하여 개발 워크플로우를 자동화하고 코드 품질을 향상시키세요! 🚀
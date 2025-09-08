---
description: '테스트 코드 생성 및 실행'
allowed-tools: ['Read', 'Write', 'Bash', 'Grep']
---

다음 코드에 대한 포괄적인 테스트를 작성해주세요:

## 테스트 프레임워크

- **Jest**: 단위 테스트 및 통합 테스트
- **NestJS Testing Module**: NestJS 애플리케이션 테스트 유틸리티

## 테스트 구조 및 위치

- **단위/통합 테스트**: 각 도메인 폴더 내부에 위치 (예: `src/users/users.service.spec.ts`)
- 테스트 파일명: `*.spec.ts` 또는 `*.test.ts`

## 테스트 유형

### 1. **Unit Tests (단위 테스트)**

- Given-When-Then 형식으로 작성
- 개별 메서드/함수의 기능 검증
- 외부 의존성은 모킹 처리

### 2. **Integration Tests (통합 테스트)**

- 모듈 간 상호작용 테스트
- 실제 데이터베이스 연결 테스트 (필요시)

### 3. **Edge Cases (엣지 케이스)**

- 경계값 테스트 (null, undefined, 빈 문자열, 0 등)
- 예외 상황 및 오류 시나리오
- 비정상적인 입력값 처리

### 4. **Mocking (모킹)**

- 외부 의존성 모킹 (Prisma, AWS, Firebase 등)
- HTTP 요청/응답 모킹
- 서드파티 서비스 모킹

## 테스트 작성 규칙

### 테스트 설명 (describe/it)

- 테스트 설명은 **한국어**로 작성
- 특정 함수를 테스트할 때 함수명은 **영어 그대로** 유지
- 예: `describe('getUserProfile()', () => { ... })`

### 테스트 구조

```typescript
describe('테스트 대상 설명', () => {
  beforeEach(() => {
    // 테스트 전 초기화 작업
  });

  it('정상적인 경우를 테스트한다', () => {
    // Given: 테스트 데이터 준비
    const testData = { ... };

    // When: 테스트 대상 실행
    const result = targetFunction(testData);

    // Then: 결과 검증
    expect(result).toBe(expected);
  });

  it('예외 상황을 처리한다', () => {
    // Given: 잘못된 데이터 준비
    const invalidData = null;

    // When & Then: 예외 발생 검증
    expect(() => targetFunction(invalidData)).toThrow();
  });
});
```

### 가독성 향상

- 적절한 주석 추가로 테스트 의도 명확화
- 테스트 데이터는 명확하고 이해하기 쉽게 작성
- 복잡한 모킹은 별도 헬퍼 함수로 분리

테스트 작성 후 `npm test` 명령어로 실행하여 결과를 확인합니다.

$ARGUMENTS

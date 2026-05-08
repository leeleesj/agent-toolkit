---
name: conventional-commit
description: git 커밋을 수행하거나 커밋 메시지를 작성한다.
  "커밋해줘", "commit", "변경사항 커밋", "커밋 메시지 작성" 같은
  요청에 사용한다.
---

## 절차
1. `git diff --staged`로 스테이징된 변경사항 확인
2. 변경 내용 분석 후 적절한 type 선택
3. 커밋 메시지 작성 후 커밋 실행

## 커밋 메시지 형식
type(scope): 설명

## type
| type | 설명 |
|---|---|
| feat | 새 기능 추가 |
| fix | 버그 수정 |
| refactor | 기능 변경 없는 코드 구조 개선 (rename, remove 포함) |
| docs | 문서 수정 |
| style | 코드 포맷, 세미콜론 등 (로직 변경 없음) |
| chore | 빌드, 패키지, 설정 등 기타 작업 |
| test | 테스트 추가/수정 |
| perf | 성능 개선 |
| build | 빌드 시스템, 의존성 변경 |
| ci | CI/CD 설정 변경 |
| revert | 이전 커밋 되돌리기 |

## 언어 규칙
- 한국어: 현재형 동사 (예: "로깅 기능 추가")
- 영어: 첫 글자 대문자, 명령형 (예: "Add logging feature")

## 규칙
- 제목 50자 이내
- scope는 선택사항 (변경 대상 모듈명)
- 본문 필요시 제목 아래 빈 줄 후 작성
- 이모지 사용 금지
- 스테이징된 파일 없으면 `git status` 확인 후 사용자에게 알릴 것

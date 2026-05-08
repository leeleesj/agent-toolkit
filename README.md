# Agent-Toolkit

Claude Code 범용 개인 환경 설정 모음. Skills, Agents, Hooks, CLAUDE.md를 관리합니다.

## 구조

```
claude/
└── .claude/
    ├── CLAUDE.md          # 글로벌 개인 설정
    └── skills/            # 범용 스킬
        ├── conventional-commit/   # 커밋 메시지 작성 + 커밋
        ├── summarize-changes/     # 변경사항 요약 + 위험 감지
        ├── code-review/           # 코드 구조/품질 점검
        ├── explain-code/          # 코드 설명 + 구현 검증
        ├── create-claude-md/      # 프로젝트 CLAUDE.md 생성
        ├── update-claude-md/      # CLAUDE.md 수정/정리
        └── create-project-skill/  # 프로젝트 스킬 템플릿 생성
```

## 설치

```bash
# 1. Stow 설치
brew install stow

# 2. 레포 클론
git clone git@github.com:leeleesj/agent-toolkit.git ~/Documents/workspace/agent-toolkit

# 3. 심볼릭 링크 생성
cd ~/Documents/workspace/agent-toolkit
stow claude
```

## 새 머신 세팅

```bash
brew install stow
git clone git@github.com:leeleesj/agent-toolkit.git ~/Documents/workspace/agent-toolkit
cd ~/Documents/workspace/agent-toolkit && stow claude
```

## 스킬 추가 후 반영

```bash
cd ~/Documents/workspace/agent-toolkit
stow -R claude
```

## Skills

| 스킬 | 역할 | 호출 |
|---|---|---|
| `conventional-commit` | 커밋 메시지 작성 + 커밋 | `/conventional-commit` |
| `summarize-changes` | 변경사항 요약 + 위험 감지 | `/summarize-changes` |
| `code-review` | 코드 구조/품질 깊이 점검 | `/code-review` |
| `explain-code` | 코드 설명 + 구현 검증 | `/explain-code` |
| `create-claude-md` | 프로젝트 CLAUDE.md 초안 생성 | `/create-claude-md` |
| `update-claude-md` | CLAUDE.md 수정/정리 | `/update-claude-md` |
| `create-project-skill` | 프로젝트 스킬 템플릿 생성 | `/create-project-skill` |

# Agent-Toolkit

Claude Code 범용 개인 환경 설정 모음. Skills, Agents, Hooks, CLAUDE.md를 관리합니다.

## Structure

```
claude/
└── .claude/
    ├── CLAUDE.md            # 글로벌 개인 설정
    ├── settings.json        # Hooks 설정 (ruff 자동 실행 등)
    └── skills/
        ├── conventional-commit/   # 커밋 메시지 작성 + 커밋
        ├── summarize-changes/     # 변경사항 요약 + 위험 감지
        ├── code-review/           # 코드 구조/품질 점검
        ├── explain-code/          # 코드 설명 + 구현 검증
        ├── create-claude-md/      # 프로젝트 CLAUDE.md 생성
        ├── update-claude-md/      # CLAUDE.md 수정/정리
        └── create-project-skill/  # 프로젝트 스킬 템플릿 생성
```

---

## Setup A — Global (applies to all projects)

`~/.claude/`에 심볼릭 링크를 걸어 모든 프로젝트에서 자동으로 스킬이 적용됩니다.

### 설치

```bash
# 1. Stow 설치
brew install stow          # macOS
sudo apt install stow      # Ubuntu/Debian
sudo yum install stow      # CentOS/RHEL

# 2. 레포 클론
git clone git@github-sjlee.com:leeleesj/agent-toolkit.git <path/to/agent-toolkit>

# 3. .stowrc 설정 (머신별 1회)
#    Stow가 심볼릭 링크를 생성할 타겟 경로를 지정
cd <path/to/agent-toolkit>
echo "--target=$HOME" > .stowrc

# 4. 심볼릭 링크 생성
stow claude
```

### 스킬 추가 후 반영

```bash
cd <path/to/agent-toolkit>
stow -R claude
```

---

## Setup B — Project (applies to specific project only)

프로젝트 디렉토리의 `.claude/`에 직접 마운트해서 해당 프로젝트에서만 적용합니다.

### 설치

```bash
# 레포 클론
git clone git@github-sjlee.com:leeleesj/agent-toolkit.git <path/to/agent-toolkit>
```

### 프로젝트에 마운트

```bash
# 마운트할 프로젝트로 이동
cd <path/to/project>

# .claude 폴더 생성
mkdir -p .claude

# 심볼릭 링크 연결
TOOLKIT=<path/to/agent-toolkit>/claude/.claude
ln -s $TOOLKIT/skills .claude/skills
ln -s $TOOLKIT/CLAUDE.md .claude/CLAUDE.md
ln -s $TOOLKIT/settings.json .claude/settings.json
```

### .gitignore에 추가 (팀 레포인 경우)

```bash
cat >> .gitignore << EOF
# Claude Code 개인 설정
.claude/skills
.claude/CLAUDE.md
.claude/settings.json
EOF
```

### 다른 프로젝트에 추가할 때

위 "프로젝트에 마운트" 단계만 반복하면 됩니다.

---

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

## Hooks

| Hook | 트리거 | 동작 |
|---|---|---|
| ruff | Claude 작업 완료 시 (Stop) | 변경된 .py 파일 자동 포맷 + 린트 수정 |

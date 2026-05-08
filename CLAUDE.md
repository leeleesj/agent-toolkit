# CLAUDE.md — agent-toolkit

## 프로젝트
GNU Stow로 관리하는 Claude Code 개인 환경 설정 dotfiles 레포.
`claude/` 디렉토리를 stow하면 `~/.claude/`에 심볼릭 링크가 생성된다.

## 기술 스택
GNU Stow (심볼릭 링크 관리)

## 핵심 경로
- `claude/.claude/CLAUDE.md` — 글로벌 개인 설정 (모든 프로젝트에 적용)
- `claude/.claude/skills/` — 커스텀 스킬 모음
- `.stowrc` — stow 타겟 경로 (`~`)
- `.stow-local-ignore` — stow 제외 파일 목록

## 설계 규칙
- 스킬은 반드시 `claude/.claude/skills/스킬명/SKILL.md` 경로에 저장
- `claude/.claude/settings.json`, `settings.local.json`은 .gitignore 처리 (민감 정보)
- `claude/.claude/projects/`는 .gitignore 처리 (로컬 세션 기록)
- 스킬 추가/수정 후 `stow -R claude`로 심볼릭 링크 재생성 필요

## 참조 문서
- 스킬 포맷 가이드: `claude/.claude/skills/create-project-skill/references/skill-format.md`
- CLAUDE.md 작성 가이드: `claude/.claude/skills/create-claude-md/references/claude_md_guide.md`

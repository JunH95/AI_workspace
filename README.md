# AI Workspace

> 개인 개발 및 협업 프로젝트에서 AI 에이전트를 안전하고 고효율로 제어하기 위한 전역 규칙, 표준 워크플로우를 저장하는 중앙 관제 센터(Control Center)입니다.

---

## 📁 저장소 구조 (Directory Structure)

```text
c:\dev\ai_workspace\
├── Global/
│   ├── Rules/
│   │   └── Global-Rules.md (Windows cp949 충돌 방지 및 AI 행동 제어 마스터 규칙)
│   └── Workflows/
│       ├── brainstorm.md   (요구사항 수집 및 기획 인터뷰 스킬 - /brainstorm)
│       ├── plan.md         (영향 파일 의존성 분석 및 세부 태스크 계획 스킬 - /plan)
│       ├── implement.md    (SOLID/20라인 규칙 기반 클린 코드 구현 스킬 - /implement)
│       ├── review.md       (에러 디버깅 및 루트 원인 분석 스킬 - /review)
│       ├── handoff.md      (세션 종료 시 맥락 압축 및 인수인계서 작성 스킬 - /handoff)
│       ├── git.md          (Conventional Commits 기반 무인 Git 자동화 스킬 - /git)
│       └── rule-creator.md (프로젝트 스택 감지 및 로컬 룰 자동 세팅 스킬 - /rule-creator)
└── .gitignore
```

---

## 🛡️ 격리형 아키텍처 (Master-Local Pattern)

본 저장소(`ai_workspace`)는 전역 표준을 관리하는 **'글로벌 통제실'** 역할을 수행하며, 개별 프로젝트 폴더의 루트 디렉토리를 오염시키지 않는 설계를 가집니다.

1. **로컬 격리 (.ai/):** 
   - 개별 프로젝트(예: Dacon)에서 AI가 자동 생성하는 모든 임시 산출물(기획서, 세부 계획서, 인수인계 파일, 로컬 룰)은 프로젝트 루트를 어지럽히지 않도록 프로젝트 내부의 숨김 폴더인 `.ai/` 디렉토리 하위로 격리되어 저장됩니다.
2. **공용 깃허브 방어:**
   - 협업 프로젝트에서 동료들과의 머지 충돌(Merge Conflict)을 방지하고 커밋 내역을 깨끗하게 유지하기 위해, 각 프로젝트의 `.gitignore` 파일에 아래와 같이 `.ai/` 폴더를 등록하여 로컬에서만 격리 및 사용하도록 권장합니다.

```text
# AI Agent Local Directory
.ai/
```

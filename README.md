# AI Workspace

## 개요 (Overview)
본 저장소는 특정 LLM 인프라에 종속되지 않는 범용적인 AI 협업 환경(Model-Agnostic AI Prompt Engineering)입니다. AI의 역할(Agent), 작업 절차(Skill), 그리고 전역 규칙(Rule)을 체계적으로 분리하여 관리하는 템플릿 환경을 제공합니다.

## 목적 (Purpose)
이 워크스페이스의 핵심 목적은 다음과 같습니다:
1. **모듈화된 프롬프트 관리:** 역할을 수행하는 `Agents/`와 작업 절차를 정의하는 `Skills/`를 분리하여 필요할 때만 결합(On-demand)해 사용함으로써 컨텍스트 길이를 최적화하고 할루시네이션을 방지합니다.
2. **단일 진실 공급원(SSOT):** 코드 품질, 전역 제어 규칙을 `rule_global.md` 하나로 집중 관리하여 일관된 AI 행동과 코드 품질을 보장합니다.
3. **지속 가능한 지식 자산화:** AI와 대화하며 얻은 지식과 문제 해결 노하우를 일회성으로 휘발시키지 않고 `Docs/`에 보관하여 영구적인 스터디 자산으로 만듭니다.

---

## 디렉토리 구조 (Directory Structure)

```text
ai_workspace/
├── README.md                           # 현재 문서 (개요 및 사용법)
├── GEMINI.md                           # 저장소 확장 및 메타 관리를 위해 AI가 준수해야 할 최상위 컨트롤 규칙
├── [project_name]_handoff_state.md     # 채팅방 이주 시 컨텍스트 연속성을 유지하기 위한 상태 스냅샷 파일
├── System/                             # [Meta-Tools] 워크스페이스 구조를 관리하고 에이전트를 자동 생성하는 핵심 도구
│   ├── agent_workspace_architect.md
│   ├── skill_agent_generator.md
│   └── skill_generator.md
├── Rules/                              # 런타임 환경에 매핑되는 전역 및 도메인 규칙 공간
│   ├── rule_global.md                  # AI 코드 생성 및 런타임 제어 전역 통합 규칙 (단일 책임)
│   └── Domains/DataScience/
│       └── rule_reproducibility.md
├── Agents/                             # 특정 역할 수행을 위한 독립적 페르소나 컨텍스트 공간
│   ├── agent_tech_lead.md              # 아키텍처 및 시스템 설계 페르소나
│   ├── agent_tech_pm.md                # 비즈니스 로직 및 기획 페르소나
│   └── agent_universal_qa.md           # 코드 품질, 컴플라이언스 및 테스트 통합 검증 페르소나
├── Skills/                             # 특정 태스크 중심의 절차적 워크플로우 공간
│   ├── skill_context_handoff.md        # 채팅방 상태 압축 및 안전한 이주(Handoff) 스킬
│   ├── skill_deep_debug.md             # 에러 폭주 방지를 위한 심층 디버깅 스킬
│   ├── skill_init_project.md           # 신규 프로젝트 초기화 스킬
│   ├── skill_github_solo.md            # 1인 개발용 신속 배포 스킬
│   └── skill_github_team.md            # 팀 협업용 PR 리뷰 및 머지 스킬
└── Docs/                               # AI 기능 명세, 스터디 노트 등 지식 자산 보관 공간 (국문)
```

---

## 활용 가이드 (How to Use)

### 1. 전역 규칙 및 환경 설정 (Rule Consolidation)
본 워크스페이스는 단일화된 **`rule_global.md`**를 최우선으로 적용받습니다. 코드 작성, 디버깅 파이프라인, 응답 형식 등 모든 기본 동작은 이 전역 규칙의 통제를 받습니다. 특정 도메인(예: Data Science) 작업 시에는 `Rules/Domains/` 하위의 규칙만 추가로 호출하여 사용합니다.

### 2. 메타 도구를 활용한 확장 (Meta-Management)
단순히 파일을 복사하는 것을 넘어, **`System/`** 디렉토리의 메타 도구를 활용하여 워크스페이스를 유기적으로 확장합니다.
- **새로운 페르소나가 필요할 때:** `@agent_workspace_architect.md`와 `@skill_agent_generator.md`를 호출하여 표준 포맷에 맞는 Agent 명세서를 자동 생성시킵니다.
- **새로운 워크플로우가 필요할 때:** `@skill_generator.md`를 통해 구조화된 Skill을 생성합니다.

### 3. 실전 프로젝트 운용 및 이주 (Deployment & Handoff)
새로운 프로젝트를 시작할 때 이 `ai_workspace`를 뼈대로 사용(Clone)합니다.
- **On-demand 소환:** 평소에는 규칙만 활성화해 두고, 특정 작업(예: 아키텍처 설계, 디버깅)이 필요할 때만 해당하는 `@Agent`와 `@Skill`을 입력창에서 맨션하여 그 순간에만 전담 전문가로 빙의시킵니다.
- **안전한 컨텍스트 이주 (Handoff):** 채팅방이 길어지거나 너무 많은 코드를 읽어 컨텍스트가 오염되었을 때는 `@skill_context_handoff.md`를 호출하세요. AI가 현재까지의 진행 상황과 미해결 과제를 `[project_name]_handoff_state.md`에 요약해 줍니다. 이후 새로운 깨끗한 채팅방을 열어 해당 파일만 맨션하면 즉시 이전 맥락을 완벽하게 이어받을 수 있습니다.
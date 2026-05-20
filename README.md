# AI Workspace

> Model-Agnostic AI Prompt Engineering & Agent Environment Configuration
> 특정 LLM 인프라에 종속되지 않는 범용적 AI 협업 환경 구축과 더불어, **AI 기능 탐구 및 개인화된 프롬프트 엔지니어링 스터디 노트를 기록하고 자산화하는 종합 지식 허브(Knowledge Hub)**입니다.

---

## 저장소 핵심 가치 (Core Value)

1. **지식의 자산화 (Knowledge Management):** AI와 대화하며 깨달은 슬래시 커맨드 활용법, 아키텍처 설계법, 프롬프트 한계점 등을 단순한 대화 휘발성으로 두지 않고 `Docs/`에 문서화하여 영구적인 스터디 자산으로 만듭니다.
2. **지속적 진화 (Continuous Evolution):** 학습한 내용을 바탕으로 기존의 에이전트(Persona)와 스킬(Workflow)을 지속적으로 버전업(Refactoring)하여 나만의 최적화된 도구로 발전시킵니다.
3. **인프라 독립성 확보 (Model-Agnostic Architecture):** 다양한 LLM 엔진 전환 시에도 동일한 동작을 보장하는 독립적 프롬프트 프레임워크를 지향합니다.
4. **런타임 및 토큰 최적화 (Context & Token Efficiency):** 전체 규칙을 상주시키지 않고, 작업 도메인에 따라 필요한 에이전트와 워크플로우를 동적으로 조립(Decoupling)하여 토큰 소모를 최적화합니다.

## 디렉토리 구조 (Directory Structure)

ai_workspace/
├── README.md               # 저장소 개요 및 활용 가이드라인
├── GEMINI.md               # 저장소 관리, 확장, 문서화 시 AI가 준수해야 할 메타 컨트롤러 (영문)
├── handoff_state.md        # [NEW] 채팅방 이주 시 컨텍스트 연속성을 유지하는 상태 스냅샷 파일
├── Docs/                   # AI 기능 명세, 스터디 노트, 아키텍처 이론 등 학습 자료 보관 공간 (국문)
├── Rules/                  # 전역 런타임 환경에 상시 매핑되는 기본 규칙 공간 (영문)
│   ├── rule_global.md      # AI 코드 생성 및 런타임 제어 전역 규칙
│   └── rule_clean_code.md  # [NEW] AI의 스파게티 코드를 차단하는 코드 품질 및 포맷 규칙
├── Agents/                 # 특정 역할 수행을 위한 독립적 페르소나 컨텍스트 공간 (영문)
│   ├── agent_product_manager.md # 비즈니스 로직 및 PRD 기획 페르소나
│   ├── agent_tech_lead.md       # 데이터베이스 및 아키텍처 설계 페르소나
│   ├── agent_hybrid_tech_pm.md  # 1인 개발 환경에 최적화된 올인원 기획 페르소나
│   └── agent_qa_engineer.md     # [NEW] 예외 상황 검증, 테스트 코드 작성 전담 페르소나
└── Skills/                 # 특정 태스크 중심의 절차적 워크플로우 공간 (영문)
    ├── skill_agent_generator.md # 커스텀 에이전트 자동 생성 스킬
    ├── skill_generator.md       # 신규 스킬 자동 생성 스킬
    ├── skill_github_solo.md     # 1인 개발용 신속 안전 배포 스킬
    ├── skill_github_team.md     # 팀 협업용 PR 리뷰 및 머지 스킬
    ├── skill_context_handoff.md # 채팅방 상태 압축 및 이전 스킬
    └── skill_deep_debug.md      # [NEW] 에러 폭주 방지 심층 디버깅 스킬

---

## 활용 가이드 (How to Use & Lifecycle)

본 저장소는 '학습 -> 자산화 -> 적용'의 생애주기(Lifecycle)를 따릅니다.

### 1. 학습 및 문서화 (Study & Documentation)
새로운 AI 기능(예: `/grill-me` 명령어)이나 효율적인 프롬프트 작성법을 깨달았을 때, AI에게 해당 내용을 `Docs/` 디렉토리에 마크다운 문서로 정리하도록 지시합니다. (예: `Docs/antigravity_slash_commands.md`)

### 2. 에이전트 및 스킬 고도화 (Evolution)
`Docs/`에 누적된 지식을 바탕으로, 더 똑똑한 에이전트나 워크플로우가 필요할 경우 인터넷의 오픈소스 프롬프트를 참고하여 `Agents/`나 `Skills/` 디렉토리에 영문으로 된 실행 명세서를 생성합니다.

### 3. 실전 프로젝트 적용 방법 (Use Case: 자율주행 탱크 프로젝트)
본 저장소(`ai_workspace`)는 프롬프트 마스터 저장소 역할을 하며, 실제 개별 프로젝트 진행 시 아래와 같이 조합하여 활용합니다.

*   **Rules (전역 규칙):** C++/Python 코딩 표준, ROS2 통신 규약 (예: `rule_cpp_standard.md`)
*   **Agents (페르소나):** `@Agents/agent_ros2_expert.md`, `@Agents/agent_cv_engineer.md`
*   **Skills (워크플로우):** `@Skills/skill_sensor_calibration.md`
*   **프로젝트 이식 방법 (Full Clone):** 마크다운 텍스트 파일은 아무리 많아도 AI의 토큰(Token)이나 성능에 부하를 주지 않으므로 필요한 것만 골라낼 필요가 없습니다. 새 프로젝트를 시작할 때는 이 `ai_workspace` 템플릿을 **통째로 클론(Clone)**하여 기본 뼈대로 사용하십시오.
*   **온디맨드 소환:** 평소에는 조용히 두다가 코딩할 때 필요한 파일만 `@` 기호로 호출하여 AI를 그 순간에만 해당 분야 최고 전문가로 빙의시킵니다.
*   **로컬 자산 분리 전략:** 특정 프로젝트(예: 블록체인)에서만 쓰이는 워커 에이전트는 해당 프로젝트 내부에만 추가하고, "어느 프로젝트에서나 쓸 만큼 엄청나게 유용한 스킬"을 개발했을 때만 이 베이스 템플릿으로 역병합(Backport)하여 도구상자를 성장시키세요.
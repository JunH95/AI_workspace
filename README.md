# AI Workspace

> Model-Agnostic AI Prompt Engineering & Agent Environment Configuration
> 특정 LLM 인프라에 종속되지 않는 범용적 AI 협업 환경 구축과 프롬프트 엔지니어링 자산화를 위한 환경설정(Configuration as Code) 저장소입니다.

---

## 저장소 구축 목적 (Core Value)

1. **인프라 독립성 확보 (Model-Agnostic Architecture):** Gemini, Claude, GPT 등 다양한 LLM 엔진 전환 시에도 동일한 동작과 출력을 보장하는 독립적 프롬프트 프레임워크를 지향합니다. 모든 지침은 이식성이 높은 순수 마크다운(.md) 포맷으로 관리됩니다.
2. **런타임 및 토큰 최적화 (Context & Token Efficiency):** 전체 규칙을 단일 세션에 무분별하게 상주시키는 비효율을 제거하고, 작업 도메인에 따라 필요한 에이전트(Persona)와 워크플로우(Skill)를 동적으로 조립(Decoupling)하여 토큰 소모를 최적화합니다.
3. **동기화 유연성 (Runtime Mapping):** Gemini CLI 및 Antigravity 등 단일 환경설정 파일(~/.gemini/GEMINI.md)을 참조하는 로컬 런타임 특성을 반영하여, 전역 규칙의 관리 효율성과 타 LLM 도구로의 확장성을 동시에 확보합니다.

## 디렉토리 구조 (Directory Structure)

ai_workspace/
├── README.md               # 저장소 개요 및 활용 가이드라인
├── GEMINI.md               # 저장소 관리 및 확장 시 AI가 준수해야 할 개발 규칙
├── Rules/                  # 전역 런타임 환경에 상시 매핑되는 기본 규칙 공간
├── Agents/                 # 특정 역할 수행을 위한 독립적 페르소나 컨텍스트 공간
└── Skills/                 # 특정 태스크 중심의 절차적 워크플로우 공간

---

## 활용 가이드 (How to Use)

본 저장소의 자산은 모든 세션에 한꺼번에 로드하지 않고, 현재 작업의 목적에 따라 **동적으로 조합하여 사용**함으로써 토큰 효율을 극대화합니다.

### 1. 전역 설정 (Global Initialization)
새로운 AI 세션을 시작할 때, `Rules/global_rules.md`의 내용을 컨텍스트에 입력하여 기본적인 답변 스타일과 코딩 표준을 확립합니다.

### 2. 에이전트 및 스킬 로드 (Loading Components)
수행하려는 태스크에 따라 필요한 파일을 선별적으로 호출합니다.
- **예시 (데이터 분석 작업):**
  1. `Rules/global_rules.md` (기본 규칙)
  2. `Agents/data_analyst.md` (데이터 분석 페르소나)
  3. `Skills/data_cleaning_pipeline.md` (데이터 정제 워크플로우)

### 3. 확장 및 기여 (Expansion)
새로운 에이전트나 스킬을 추가하고 싶다면, `GEMINI.md`의 생성 규격을 준수하여 새로운 마크다운 파일을 생성하도록 AI에게 요청하세요. 모든 변경 사항은 사전에 사용자 브리핑을 거쳐 수행됩니다.
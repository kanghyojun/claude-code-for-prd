# PRD Agents 가이드

기획자를 위한 Claude Code agents, commands, skills를 정의한 리포지토리입니다.

## 목차

- [개요](#개요)
- [Agents](#agents)
- [Commands](#commands)
- [Skills](#skills)
- [사용 방법](#사용-방법)
- [설치](#설치)

## 개요

이 리포지토리는 제품 기획자(Product Manager)가 Claude Code를 통해 효율적으로 문서를 작성하고 제품 전략을 수립할 수 있도록 돕는 도구들을 제공합니다.

### 구성 요소

- **Agents**: 자율적으로 복잡한 작업을 수행하는 에이전트
- **Commands**: 특정 작업을 실행하는 슬래시 커맨드
- **Skills**: 도메인 전문 지식을 제공하는 스킬

## Agents

Agents는 사용자의 입력을 바탕으로 자율적으로 문서를 생성하거나 분석하는 에이전트입니다.

### PRD Generator (`agents/prd-generator.md`)

**용도**: 사용자 입력을 바탕으로 포괄적인 Product Requirements Document (PRD)를 생성

**주요 기능**:
- 문제와 기회 명확하게 정의
- 솔루션 접근 방식 제시
- 엔지니어링 및 디자인 팀을 위한 실행 가능한 가이드 제공
- 이해관계자 리뷰 및 팀 실행이 가능한 상태의 문서 생성

**생성하는 문서 섹션**:
- 📋 Overview (TL;DR, Problem Statement, Goals, Non-Goals)
- 🎯 Strategy & Context (Why Now?, Success Metrics, Strategic Alignment)
- 👥 Users & Personas
- 💡 Solution (Product Vision, User Flows, Key Features)
- 🔧 Technical Approach
- 🚀 Execution Plan (Phasing, Timeline, Dependencies)
- ⚠️ Risks & Mitigations
- 📊 Launch Plan

**사용 시기**: 새로운 제품이나 기능에 대한 완전한 PRD가 필요할 때

### User Stories Generator (`agents/user-stories-generator.md`)

**용도**: PRD나 기능 스펙으로부터 포괄적인 user story를 생성

**주요 기능**:
- INVEST 원칙 준수 (Independent, Negotiable, Valuable, Estimable, Small, Testable)
- Given-When-Then 형식의 상세한 acceptance criteria
- Edge case 및 에러 처리 고려
- 스프린트 계획 및 추정 가능한 형태

**생성하는 내용**:
- Epic Overview
- User Story 상세 (User Story, Description, Acceptance Criteria, Technical Notes)
- Story Summary Table
- Dependency Visualization
- Sprint Recommendations

**사용 시기**: PRD를 실행 가능한 개발 스토리로 변환해야 할 때

### Tasks Generator (`agents/tasks-generator.md`)

**용도**: User story를 실행 가능한 개발 task와 GitHub issue로 변환

**주요 기능**:
- 작업을 관리 가능한 단위로 분해
- 명확한 컨텍스트와 acceptance criteria 제공
- GitHub/Jira/Linear 등으로 바로 import 가능한 형식
- 기술적 구현 가이드 포함

**생성하는 내용**:
- Task Summary Table (ID, Title, Type, Priority, Size, Dependencies)
- 상세 Task 정의 (Description, Acceptance Criteria, Technical Approach, Implementation Details)
- API Contract 및 Database Schema
- Sprint별 Task 분류
- GitHub Issues 형식 출력

**사용 시기**: User story를 구체적인 개발 작업으로 분해해야 할 때

## Commands

Commands는 특정 작업을 실행하는 슬래시 커맨드입니다.

### /prd-review (`commands/prd-review.md`)

**용도**: PRD 문서를 검토하고 구조화된 피드백 제공

**주요 기능**:
- PRD 완성도 체크리스트 검증
- 품질 평가 (문제 정의 명확성, 솔루션 명확성, 범위 명확성)
- 중대한 이슈 식별 (Red flags, Yellow flags)
- 긍정적 신호 강조
- 실행 가능한 권장사항 제공

**검토 영역**:
- 문제 & 맥락
- 목표 & 비목표
- 솔루션 & 사용자 경험
- 성공 지표
- 기술적 접근
- 타임라인 & 실행

**사용 방법**:
```
/prd-review
```

사용자에게 PRD 파일 경로와 특별히 검토받고 싶은 사항을 질문한 후 상세한 피드백을 제공합니다.

## Skills

Skills는 특정 도메인에 대한 전문 지식을 제공하는 가이드입니다.

### Persona Development (`skills/persona.md`)

**용도**: 제품 개발을 위한 사용자 페르소나 정의 지원

**주요 기능**:
- 제품 맥락 이해
- 페르소나 카테고리 식별 (2-4개)
- 각 페르소나별 상세 프로필 생성

**페르소나 구성 요소**:
- 인구통계 & 배경 (역할, 회사 규모, 경험 수준)
- 행동적 특성 (현재 문제 해결 방법, 사용 도구)
- 목표 & 동기
- 페인 포인트 & 불만사항
- 니즈 & 기대사항

**사용 시기**: 제품의 타겟 사용자를 명확하게 정의해야 할 때

### Competitive Analysis (`skills/competitive-analysis.md`)

**용도**: 철저한 경쟁사 분석 수행 지원

**주요 기능**:
- 경쟁 환경 정의 (직접/간접 경쟁사, 대안 솔루션)
- 경쟁사별 상세 분석 (회사 포지션, 제품, GTM 전략, 강점/약점)
- 비교 분석 (기능, 가격, 포지셔닝)
- 전략적 인사이트 도출

**분석 결과**:
- 시장 갭 식별
- 경쟁 위협 파악
- 차별화 기회 발견
- 전략적 권장사항 (방어/차별화/무시/혁신 영역)

**사용 시기**: 시장 기회를 파악하거나 제품 전략을 수립할 때

### Problem Analysis (`skills/problem-analysis.md`)

**용도**: 올바른 문제를 해결하고 있는지 확인하기 위한 깊이 있는 문제 분석

**핵심 철학**: "좋은 PM은 솔루션이 아닌 문제와 사랑에 빠집니다"

**주요 기능**:
- 명확하고 구체적인 문제 정의
- 문제 검증 (존재 증거, 중요성, 시장 규모)
- 근본 원인 분석 (Five Whys)
- 현재 솔루션 및 갭 분석
- 성공 메트릭 정의

**분석 프로세스**:
1. 문제 정의 (누가, 무엇으로 어려움을 겪는가, 언제, 영향, 현재)
2. 문제 검증 (증거, 중요성, 시장 규모)
3. 근본 원인 분석 (Five Whys, 문제 분해)
4. 현재 솔루션 분석
5. 문제 범위 및 경계 설정
6. 성공 메트릭 정의

**사용 시기**: 새로운 제품/기능 개발을 시작하기 전, 문제를 명확히 정의하고 검증해야 할 때

## 사용 방법

### 전형적인 워크플로우

#### 1. 문제 분석 단계
```
"Problem Analysis 스킬을 사용해서 [문제 영역]에 대한 문제 분석을 도와줘"
```
- Problem Analysis 스킬로 문제를 정의하고 검증
- Persona 스킬로 타겟 사용자 정의
- Competitive Analysis 스킬로 시장 환경 이해

#### 2. PRD 작성 단계
```
[PRD Generator 에이전트 사용]
```
- 수집한 정보를 바탕으로 PRD Generator 에이전트가 완전한 PRD 생성
- /prd-review 커맨드로 작성된 PRD 검토 및 개선

#### 3. 실행 계획 단계
```
[User Stories Generator 에이전트 사용]
```
- PRD를 User Stories Generator 에이전트로 전달하여 user story 생성

#### 4. 개발 태스크 분해
```
[Tasks Generator 에이전트 사용]
```
- User story를 Tasks Generator 에이전트로 전달하여 개발 task 생성
- GitHub/Jira 등에 import

### 예시 시나리오

**시나리오**: 새로운 팀 협업 기능 개발

1. **문제 분석**: "Problem Analysis 스킬로 원격 팀의 협업 어려움을 분석해줘"
2. **페르소나 정의**: "Persona 스킬로 타겟 사용자 페르소나를 만들어줘"
3. **경쟁사 분석**: "Competitive Analysis 스킬로 Slack, Microsoft Teams, Discord를 분석해줘"
4. **PRD 생성**: PRD Generator 에이전트로 "팀 협업 기능에 대한 PRD를 작성해줘"
5. **PRD 검토**: `/prd-review`로 작성된 PRD 검토
6. **User Story 생성**: User Stories Generator 에이전트로 user story 생성
7. **Task 분해**: Tasks Generator 에이전트로 개발 task 생성

## 설치

이 리포지토리의 내용을 Claude Code에서 사용하려면:

### 방법 1: 직접 복사
1. 이 리포지토리를 클론: `git clone [repository-url]`
2. `.claude` 디렉토리를 홈 디렉토리나 프로젝트 루트에 복사
3. 필요한 agents, commands, skills를 `.claude/` 디렉토리 구조에 맞게 배치

### 방법 2: 심볼릭 링크 (권장)
```bash
# 글로벌 설정 (모든 프로젝트에서 사용)
ln -s /path/to/prd-agents/agents ~/.claude/agents
ln -s /path/to/prd-agents/commands ~/.claude/commands
ln -s /path/to/prd-agents/skills ~/.claude/skills

# 또는 프로젝트별 설정
mkdir -p .claude
ln -s /path/to/prd-agents/agents .claude/agents
ln -s /path/to/prd-agents/commands .claude/commands
ln -s /path/to/prd-agents/skills .claude/skills
```

### 디렉토리 구조
```
.claude/
├── agents/
│   ├── prd-generator.md
│   ├── user-stories-generator.md
│   └── tasks-generator.md
├── commands/
│   └── prd-review.md
└── skills/
    ├── persona.md
    ├── competitive-analysis.md
    └── problem-analysis.md
```

## 베스트 프랙티스

### PRD 작성 시
- ✅ 증거에 기반한 명확한 문제 정의
- ✅ 측정 가능하고 의미 있는 성공 메트릭
- ✅ 범위 경계 명시 (Goals와 Non-Goals)
- ✅ Acceptance criteria가 포함된 user story
- ❌ 모호한 표현 지양 ("개선", "더 나은", "원활한")
- ❌ 불필요한 구현 디테일 과도하게 명시하지 않기

### User Story 작성 시
- ✅ INVEST 원칙 준수
- ✅ Given-When-Then 형식의 명확한 acceptance criteria
- ✅ Edge case 및 에러 처리 포함
- ✅ 한 스프린트에 완료 가능한 크기
- ❌ 너무 크거나 너무 작게 만들지 않기
- ❌ "so that" 생략하지 않기

### Task 분해 시
- ✅ 독립적으로 완료 가능한 단위
- ✅ 명확한 acceptance criteria
- ✅ 구현 가이드 포함
- ✅ 최대 1-3일 내 완료 가능
- ❌ 너무 세분화하지 않기
- ❌ 비기능적 요구사항 무시하지 않기

## 기여하기

새로운 agents, commands, skills를 추가하거나 기존 것을 개선하려면:

1. 이 리포지토리를 포크
2. 새로운 브랜치 생성 (`git checkout -b feature/new-agent`)
3. 변경사항 커밋 (`git commit -am 'Add new agent for X'`)
4. 브랜치에 푸시 (`git push origin feature/new-agent`)
5. Pull Request 생성

## 라이선스

[라이선스 정보 추가 필요]

## 참고 자료

- [Claude Code 공식 문서](https://docs.claude.com/en/docs/claude-code)
- [Product Management 베스트 프랙티스](https://www.productplan.com/learn/product-management-best-practices/)
- [INVEST 원칙](https://en.wikipedia.org/wiki/INVEST_(mnemonic))

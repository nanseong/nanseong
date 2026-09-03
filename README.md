# 권환성

### AI Engineer | LLM · RAG · Knowledge Graph · Machine Learning

데이터를 분석하는 것에서 끝나지 않고,  
**검색 → 생성 → 검증 → 서비스**까지 연결되는 AI 시스템을 개발합니다.

LLM과 Machine Learning을 활용해 실제 문제를 해결하고,  
모델의 결과를 신뢰할 수 있는 서비스로 만드는 과정에 관심이 있습니다.

---

## About Me

사진과 뉴미디어아트를 전공하며 **사용자에게 정보를 어떻게 전달할 것인가**를 고민해왔고,  
현재는 그 경험을 AI 기술과 결합해 **데이터에서 사용자 경험까지 이어지는 서비스**를 개발하고 있습니다.

특히 LLM 기반 서비스에서 단순히 모델을 호출하는 것보다  
**데이터 품질, 검색 정확도, 생성 결과 검증, 재현 가능한 파이프라인**을 중요하게 생각합니다.

주요 관심 분야는 **RAG, Knowledge Graph, Multi-Agent System, Machine Learning, AI 기반 개인화 서비스**입니다.

---

## Core Competencies

| 영역 | 역량 |
|---|---|
| **LLM · RAG** | 문서 전처리, Embedding, Hybrid Search, Reranking, Prompt Engineering, 생성 결과 검증 |
| **Knowledge Graph** | Entity 정규화, Relationship 설계, Graph Search, Neo4j 기반 지식그래프 구축 |
| **Multi-Agent** | Agent 역할 분리, State 관리, Routing, Validator, Retry/Fallback 흐름 설계 |
| **Machine Learning** | 데이터 전처리, Feature Engineering, 분류 모델 학습, 성능 평가 및 개선 |
| **Data Pipeline** | 정형·비정형 데이터 정제, 자동 검증, 재현 가능한 데이터 처리 파이프라인 |
| **Backend · DB** | Django, REST API, PostgreSQL, pgvector, Neo4j 기반 AI 서비스 연동 |
| **AI Evaluation** | Precision·Recall·F1, RAGAS, Golden Set, Rule-based Validation 기반 품질 평가 |

---

## Tech Stack

### AI / LLM
`Python` `LangChain` `LangGraph` `OpenAI API` `RAG` `Multi-Agent`  
`Prompt Engineering` `RAGAS` `Hugging Face`

### Machine Learning
`Scikit-learn` `PyTorch` `Pandas` `NumPy`

### Database / Search
`PostgreSQL` `pgvector` `Neo4j` `Hybrid Search` `Vector Search`

### Backend / Infrastructure
`Django` `REST API` `Docker` `Git`

---

# Featured Projects

## 🇰🇷 HIMATE — AI 기반 한국사 학습 플랫폼

`LLM` `RAG` `Knowledge Graph` `Machine Learning` `Neo4j` `PostgreSQL` `pgvector`

한국사능력검정시험 학습 데이터를 기반으로  
**취약점 진단 → 맞춤 문제 → AI 해설 → 학습 계획 → 주간 리포트**까지 연결한 개인화 AI 학습 플랫폼입니다.

### 주요 기여

- 한국사 데이터 기반 **Neo4j Knowledge Graph 구축**
- 약 **19,000개 Entity / 40,000개 Relationship** 규모의 그래프 데이터 구성
- 동명이인·이명·중복 Entity 처리를 위한 정규화 및 병합 검증 로직 설계
- PostgreSQL + pgvector 기반 **Hybrid RAG 검색 구조 구현**
- Dense/Sparse Retrieval 및 Reranker 기반 검색 성능 개선
- 학습자의 오답 데이터를 활용한 **취약점 분석 로직 구현**
- 취약점 기반 7일 학습 계획 및 AI 주간 리포트 생성
- 한국사 문제 자동 생성 및 품질 검증 파이프라인 구축

### 문제 해결

여러 출처의 한국사 데이터에는 동일 이름을 가진 인물과 서로 다른 표기의 Entity가 존재했습니다.

단순 문자열 비교를 사용하면 서로 다른 인물이 하나로 병합될 수 있기 때문에,

> **Precision > Recall**

을 기준으로 병합 전략을 설계했습니다.

한자·시대·생몰년·출처 등의 조건을 검증하고,  
LLM은 병합 후보만 제안하며 **최종 판단은 코드 기반 검증 로직이 수행하도록 구성**했습니다.

### 성과

- Knowledge Graph Entity 약 **19,000개**
- Fact Relationship 약 **40,000건**
- Golden Set 기준 **오병합 0건**
- Entity Coverage **89.2%**
- 판정 일치도 **0.99**

RAG 검색에서도 Top-K와 Reranker를 조정하여

- Context Precision **0.72 → 0.83**
- Context Recall **0.79 → 0.87**
- Faithfulness **0.90 → 0.94**
- Answer Relevance **0.82 유지**

의 결과를 확인했습니다.

---

## 🤖 한국사 문제 자동 생성 Pipeline

`LLM` `SLLM` `Prompt Engineering` `Validation` `Checkpoint`

LLM과 SLLM을 활용하여 한국사 5지선다 문제를 대량 생성하고,  
생성 결과를 자동으로 검증하는 파이프라인을 개발했습니다.

### Architecture

```text
Closed JSON Pack
        ↓
GPT 지문 · 발문 생성
        ↓
SLLM 선택지 생성
        ↓
Local Gate Validation
        ↓
LLM Evaluation
        ↓
부분 재생성 / Repair
        ↓
해설 생성
        ↓
Database
```

### 주요 기여

- 지문·발문·정답·오답을 독립적인 State로 관리
- 실패한 구성 요소만 다시 생성하는 **Partial Retry 구조 구현**
- Checkpoint 기반 중단·재개 기능 설계
- 생성 결과 검증을 위한 **6개 Gate Validation 구조 설계**
- 일반 선택지는 SLLM, 복잡한 구성은 GPT를 활용하는 모델 분리
- 평가 결과의 Feedback을 재생성 Prompt에 전달하는 구조 구현

### 문제 해결

초기 구조에서는 50개의 문제 중 마지막 문제 하나가 실패해도  
전체 문제를 처음부터 다시 생성해야 했습니다.

이를

```text
문항 단위 재생성
        ↓
구성 요소 단위 재생성
```

구조로 변경했습니다.

예를 들어 `오답 ③`만 평가에 실패하면  
지문이나 다른 선택지는 유지하고 **오답 ③만 Feedback과 함께 다시 생성**합니다.

이를 통해 불필요한 LLM 호출을 줄이고 대량 문제 생성에 적합한 구조로 개선했습니다.

---

## 🔍 Knowledge Graph 기반 오답 생성

`Neo4j` `Knowledge Graph` `Graph Search` `LLM`

정답과 역사적으로 유사하지만 실제로는 틀린 선택지를  
Knowledge Graph에서 탐색하여 자동 생성하는 시스템입니다.

### 핵심 아이디어

```text
정답 Entity
    ↓
Knowledge Graph 탐색
    ↓
동일 시대 / 유형 / 관계 후보
    ↓
오답 후보 추출
    ↓
Validation
```

Graph의 Hop Distance를 활용하여 문제 난이도를 조절했습니다.

| Graph Distance | 난이도 |
|---|---|
| 1-Hop | 쉬움 |
| 2-Hop | 보통 |
| 3-Hop | 어려움 |

설정된 난이도와 Graph Distance가 일치하지 않으면  
해당 선택지의 생성을 차단하도록 구성했습니다.

---

## 📊 한국사 기출 Trend Analysis ML

`Machine Learning` `Classification` `Data Pipeline` `Feature Engineering`

한국사 기출문제를 자동으로 분류하여  
**시대·주제별 출제 경향을 구조화하는 Machine Learning Pipeline**을 개발했습니다.

단순 문제 예측기가 아니라

```text
기출 문제
   ↓
자동 Labeling
   ↓
시대 / 주제 분류
   ↓
출제 Trend 집계
   ↓
학습 계획 / 문제 생성
```

으로 이어지는 데이터 처리 시스템을 목표로 했습니다.

### Model Performance

| 분류 | Macro F1 |
|---|---:|
| 시대 분류 | **0.93** |
| 통합 주제 분류 | **0.85** |
| 세부 주제 분류 | **0.70** |

데이터 Labeling 체계를 개선하여  
Macro F1을 최대 **+0.37** 향상시켰습니다.

분석 결과는 개인화 학습 계획과 문제 생성 시스템에서 활용할 수 있도록 연결했습니다.

---

## 🛡️ AI 문제 품질 검수 ML

`Machine Learning` `Classification` `Quality Control`

AI가 생성한 문제를 자동으로 폐기하는 것이 아니라,  
**검수가 필요한 선택지를 먼저 찾아주는 ML 모델**을 개발했습니다.

```text
문제 자동 폐기        ❌
정답 예측             ❌

오류 의심 선택지 탐지  ✅
검수 우선순위 제공     ✅
```

문항 전체가 아닌 **선택지 단위 Binary Classification**으로 문제를 정의했습니다.

이를 통해 검수자가 모든 문제를 동일하게 확인하는 대신  
오류 가능성이 높은 선택지를 우선적으로 검토할 수 있도록 설계했습니다.

---

## What I Focus On

제가 AI 프로젝트에서 중요하게 생각하는 것은  
**모델을 사용하는 것보다 모델의 결과를 신뢰할 수 있게 만드는 것**입니다.

```text
Data
 ↓
Retrieval
 ↓
Generation
 ↓
Validation
 ↓
Service
```

각 단계에서 발생할 수 있는 오류를 정의하고,  
LLM의 판단에만 의존하지 않고 **Code Validation과 Evaluation Pipeline을 함께 설계**하는 것을 지향합니다.

---

## Currently Interested In

- Reliable LLM System
- Retrieval-Augmented Generation
- Knowledge Graph + LLM
- Agentic Workflow
- AI Evaluation
- Personalized AI Service
- LLM / SLLM Hybrid Architecture

---

## GitHub Activity

<!-- GitHub Stats -->

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=YOUR_GITHUB_ID&show_icons=true&hide_border=true)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_GITHUB_ID&layout=compact&hide_border=true)

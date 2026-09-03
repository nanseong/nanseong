# 👋 안녕하세요, AI Engineer 권환성입니다.

### AI · RAG · Knowledge Graph · Backend

LLM을 단순히 호출하는 것보다  
**데이터를 수집·구조화하고, 검색하고, 근거 있는 답변으로 연결하는 과정**에 관심이 있습니다.

RAG, VectorDB, Knowledge Graph, Multi-Agent를 활용한 AI 서비스를 개발하며  
**검색 품질과 생성 결과를 측정하고 개선할 수 있는 시스템**을 만드는 것을 목표로 합니다.

---

## 🛠️ Tech Stack

### Language
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)

### AI · LLM
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging_Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black)

### Data · ML
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)

### Database · Search
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=flat-square&logo=neo4j&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

### Backend · Tools
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

---

## 💡 Core Competencies

### RAG & Retrieval
- PostgreSQL · pgvector 기반 Vector Search 구축
- Dense / Sparse 검색을 결합한 Hybrid Retrieval 설계
- CrossEncoder Reranker를 활용한 검색 결과 재정렬
- RAGAS 기반 검색·답변 품질 평가 및 검색 파라미터 개선

### Knowledge Graph
- Neo4j 기반 GraphDB 스키마 설계 및 데이터 구축
- Entity · Relationship 기반 데이터 구조화
- Vector Search와 Graph Context를 결합한 검색 구조 구현
- 관계 데이터를 활용한 LLM 답변 Context 보강

### LLM Application
- 검색 근거 기반 AI Chatbot 구현
- LangGraph 기반 Multi-Agent Workflow 참여
- Agent 결과를 종합하는 Final Answer Agent 구현
- 검색 결과와 생성 답변 간 Grounding 검증

### Backend & Service
- Django 기반 웹 애플리케이션 개발
- 사용자 인증 및 Session 기반 계정 기능 구현
- AI/RAG Backend와 Frontend 연동
- 서비스 UI 설계 및 사용자 Flow 구현

---

# 🚀 Projects

## 🇰🇷 HIMATE
### AI 기반 맞춤형 한국사 학습 서비스

> 진단평가부터 맞춤 문제풀이, 오답 분석, 학습 계획,  
> 근거 기반 AI 챗봇까지 연결한 한국사 학습 플랫폼

**Role · AI/RAG · Data · Full-stack**

`Python` `Django` `PostgreSQL` `pgvector` `Neo4j` `LangChain` `OpenAI`

### 담당 영역

**한국사 학습자료 수집 및 전처리**
- 한국사 RAG에 활용할 학습 자료 수집
- 서로 다른 형태의 원천 데이터를 검색 가능한 구조로 정제
- 문서 Metadata와 검색 단위를 고려한 데이터 전처리

**PostgreSQL · pgvector Embedding Pipeline**
- 전처리된 한국사 문서를 PostgreSQL에 적재
- 문서 Chunk 단위 Vector Embedding 생성
- pgvector 기반 의미 검색 환경 구축

**Hybrid RAG Search**
- Vector Search와 Keyword Search를 결합한 Hybrid Retrieval 구성
- 검색 후보에 CrossEncoder Reranker 적용
- 질문과 관련성이 높은 Context를 선별해 LLM에 전달

```text
User Question
      │
      ▼
Query Processing
      │
 ┌────┴────┐
 ▼         ▼
Vector    Keyword
Search    Search
 │          │
 └────┬─────┘
      ▼
 Candidate Context
      │
      ▼
   Reranker
      │
      ▼
Graph Context
      │
      ▼
     LLM
      │
      ▼
Grounded Answer
```

### RAG 성능 개선

검색 문서 수를 단순히 늘리는 대신  
**Top-K 조정 + Reranker 적용**을 통해 실제 답변에 필요한 Context를 선별했습니다.

| Metric | Before | After |
|---|---:|---:|
| Context Precision | 0.72 | **0.83** |
| Context Recall | 0.79 | **0.87** |
| Faithfulness | 0.90 | **0.94** |
| Answer Relevance | 0.82 | **0.82** |

최종적으로 **Top-K 5 + Reranker** 구성에서 가장 안정적인 성능을 확인했습니다.

### GraphDB Context 연동

Vector Search만으로 설명하기 어려운 역사적 관계를 보완하기 위해  
Neo4j GraphDB의 Entity 관계 정보를 RAG Context와 연결했습니다.

```text
Vector Context
      │
      ├──────┐
      │      │
      ▼      ▼
 Documents  Graph Context
      │      │
      └──┬───┘
         ▼
     LLM Answer
```

문서 검색 결과와 인물·사건·시대의 관계 정보를 함께 활용해  
답변 생성에 필요한 Context를 확장했습니다.

### AI Chatbot

- 한국사 **개념 질문 / 문제 해설 질문** 유형 분리
- 검색 근거 기반 답변 생성
- RAG 검색 결과와 GraphDB Context를 답변에 연결
- 챗봇 화면 및 Backend 연동 구현
- 검색 → 생성 → 화면 출력까지 End-to-End 동작 검증

### Full-stack Integration

AI 기능 구현에 그치지 않고 실제 서비스에서 사용할 수 있도록

- 챗봇 UI
- 진단평가 화면
- Django Backend 연동
- RAG 응답 화면 출력
- 기능 간 Integration Test

까지 연결했습니다.

**Repository → [HIMATE](https://github.com/nanseong/HIMATE)**

---

## 🍁 MapleStory RAG Multi-Agent Chatbot
### 데이터 기반 게임 정보 검색 및 분석 AI

> 메이플스토리의 공식 API, 문서, GraphDB, Web Search를 결합해  
> 캐릭터 분석과 근거 기반 답변을 제공하는 Multi-Agent RAG Chatbot

**Role · GraphDB · Web RAG · Agent · Design**

`LangGraph` `LangChain` `Neo4j` `Tavily` `PostgreSQL` `pgvector` `Streamlit`

### 담당 영역

**GraphDB Schema & Neo4j**
- 보스 · 직업 · 장비 · 이벤트 등 게임 Entity 관계 정의
- GraphDB Schema 설계
- Neo4j 기반 관계 데이터 탐색 구조 구축

**Web Search RAG**
- 최신 공지와 이벤트처럼 내부 DB만으로 대응하기 어려운 질문을 위한 Web RAG 구현
- 검색 결과의 출처와 최신성을 유지한 Context 구성
- 내부 RAG와 외부 Web Search가 함께 사용될 수 있도록 검색 구조 설계

**Final Answer Agent**
- Research · Analytics · Calculator 등 개별 Agent 결과 수집
- 여러 Agent의 Context를 하나의 답변으로 통합
- 근거와 출처를 반영한 최종 응답 생성

```text
                 Supervisor
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
    Research     Analytics    Calculator
        │            │            │
        └────────────┼────────────┘
                     ▼
              Final Answer Agent
                     │
                     ▼
               Final Response
```

**Design**
- Streamlit 기반 서비스 UI 설계
- AI 기능이 사용자의 질문 흐름과 자연스럽게 연결되도록 화면 구성

**Repository → [SKN27-3rd-1TEAM](https://github.com/nanseong/SKN27-3rd-1TEAM)**

---

## 👻 괴이 기록 보관소
### LLM · GraphDB 기반 괴담 아카이브 서비스

> 지역별 괴담과 금기 데이터를 탐색하고  
> AI를 통해 새로운 괴담 콘텐츠를 생성할 수 있는 Django 웹 서비스

**Role · Full-stack · UI/UX**

`Python` `Django` `PostgreSQL` `JavaScript` `HTML` `CSS`

### 담당 영역

**Service UI Design**
- 프로젝트 전체 화면 UI 설계
- 괴담 아카이브 콘셉트에 맞는 사용자 경험 구성
- Django Template 기반 화면 구현

**Account System**
- 회원가입
- 로그인 / 로그아웃
- Django Session 기반 인증
- 마이페이지
- 회원탈퇴

등 사용자 계정 Flow를 구현했습니다.

```text
Sign Up
   ↓
Login
   ↓
Session Authentication
   ↓
My Page
   ↓
Logout / Delete Account
```

**금기자료실**
- `archive` 앱의 금기자료실 기능 구현
- 저장된 콘텐츠를 사용자가 탐색할 수 있는 화면 및 Backend 로직 연결

AI 기능뿐 아니라 **사용자가 실제로 서비스를 이용하기 위해 필요한 웹 기능과 UI를 직접 구현**하며 Full-stack 개발 경험을 확장했습니다.

**Repository → [SKN27-4th-1team](https://github.com/nanseong/SKN27-4th-1team)**

---

## 📊 Telco Customer Churn Analysis
### 통신사 고객 이탈 예측 및 데이터 분석 서비스

> 통신사 고객 데이터를 기반으로 이탈 위험 고객을 분석하고  
> 분석 결과를 실제 비즈니스 의사결정 화면으로 연결한 ML 프로젝트

`Python` `Pandas` `Scikit-learn` `Streamlit` `MySQL`

### Project Experience

- 통신사 고객 데이터 기반 EDA 및 ML Workflow 경험
- 고객 이탈 예측 결과를 서비스 화면과 연결
- Streamlit 기반 데이터 서비스 개발
- MySQL을 활용한 서비스 데이터 관리
- 팀 기반 ML 프로젝트의 기획 → 분석 → 서비스 구현 과정 경험

이 프로젝트를 통해 정형 데이터 분석과 ML 서비스 개발을 경험했고,  
이후 프로젝트에서는 RAG · GraphDB · LLM 기반 AI 시스템으로 개발 영역을 확장했습니다.

**Repository → [SKN27-2nd-1TEAM](https://github.com/nanseong/SKN27-2nd-1TEAM)**

---

## 📈 Development Journey

```text
Data Analysis
     │
     ▼
Machine Learning
     │
     ▼
Web Application
     │
     ▼
Vector Search · RAG
     │
     ▼
Knowledge Graph
     │
     ▼
Multi-Agent AI System
```

정형 데이터 기반 ML 프로젝트에서 시작해  
웹 서비스, VectorDB, RAG, Knowledge Graph, Multi-Agent 시스템으로 개발 범위를 확장해왔습니다.

현재는 개별 AI 모델의 성능뿐 아니라  
**검색 → 추론 → 생성 → 검증이 하나의 서비스 안에서 안정적으로 동작하는 구조**에 관심을 두고 있습니다.

---

## 📈 GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=nanseong&show_icons=true&hide_border=true&hide_title=true)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=nanseong&layout=compact&hide_border=true)

---

### Engineering Focus

> **좋은 AI 서비스는 답변을 생성하는 것에서 끝나지 않고,  
> 그 답변이 어디에서 왔는지 설명할 수 있어야 한다고 생각합니다.**

RAG · Knowledge Graph · LLM을 중심으로  
데이터에서 검색하고, 관계를 찾고, 근거 있는 결과를 사용자에게 전달하는  
**신뢰할 수 있는 AI 서비스를 개발하고 있습니다.**

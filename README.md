# 👋 안녕하세요, 박화랑입니다

### AI를 실제 서비스로 연결하는 AI / LLM Application Developer

LLM, Computer Vision, Backend 기술을 활용해  
**AI 기능을 실제 서비스 형태로 구현하고 성능을 개선하는 개발자**를 지향합니다.

LangGraph 기반 AI Workflow 설계부터  
Spring Boot · FastAPI 백엔드 개발, Edge AI 최적화와 배포까지  
서비스의 End-To-End 개발 과정을 경험했습니다.

---

## 🙋‍♂️ About Me

- 🤖 **LLM · RAG · LangGraph**를 활용한 AI Workflow와 검색 파이프라인을 개발했습니다.
- ⚙️ **Spring Boot · FastAPI** 기반의 Backend 및 AI Serving API를 개발했습니다.
- 🔍 Text-to-SQL, 멀티모달 검색, 추천 등 **AI 기반 검색 시스템**에 관심이 있습니다.
- 👁️ YOLO · OCR · TensorRT를 활용한 **Computer Vision / Edge AI Pipeline**을 구축했습니다.
- 🚀 AI 모델 자체뿐 아니라 **병목 분석과 성능 최적화**를 통해 실제 서비스에 적용하는 과정에 관심이 있습니다.
- 🐳 Docker · AWS · Jenkins를 활용한 서비스 배포 및 운영 환경을 경험했습니다.

---

# 🚀 Featured Projects

## 🏠 [서집사](https://github.com/SKNETWORKS-FAMILY-AICAMP/SKN04-FINAL-1Team)

### 자연어 조건 기반 부동산 추천 AI 챗봇

사용자가 원하는 부동산 조건을 자연어로 입력하면  
AI가 조건을 분석하고 DB 조회 결과를 기반으로 적합한 매물을 추천하는 서비스입니다.

### 🔧 담당 역할

- LangGraph 기반 AI Pipeline 설계
- 사용자 질문 필터링 및 매매 / 전월세 분기 처리
- Text-to-SQL Prompt 개선
- SQL 정제 및 DB 조회 기반 추천 응답 생성
- 멀티턴 대화 요약 및 Streaming 응답 적용
- ChromaDB 기반 Question-SQL Retrieval 구성

### 💡 Problem Solving

기존 단순 Text-to-SQL 구조에서는  
'역세권', '도보 시간', '엘리베이터'처럼 의미 해석이 필요한 자연어 조건에서  
DB 구조와 맞지 않는 SQL이나 Hallucination이 발생했습니다.

이를 해결하기 위해 TAG(Table-Augmented Generation)의  
**Query Synthesis 개념을 부동산 도메인에 적용**했습니다.

- 자연어 표현을 DB 조건으로 변환하는 Domain Rule 정의
- KoSBERT 기반 질문 Embedding
- ChromaDB에서 유사 Question-SQL Pair 검색
- `User Question + DB Schema + Domain Rule + Similar SQL Example` 구조로 Prompt 개선

이를 통해 복잡한 자연어 조건에서도  
실제 DB 구조에 맞는 SQL을 생성할 수 있도록 Pipeline을 개선했습니다.

### 🛠 Tech Stack

`Python` `LangGraph` `LangChain` `OpenAI API`  
`RAG` `Text-to-SQL` `FastAPI` `PostgreSQL` `ChromaDB`

---

## 📚 [도도 (도서관 도우미)](https://github.com/hwarange/DODO)

### 도서관 오배열 탐지 AIoT 서비스

로봇이 도서관 서가를 순회하며 촬영한 영상을 분석해  
잘못 배치된 도서를 탐지하고 사서용 Dashboard에 결과를 제공하는 AIoT 서비스입니다.

### 🔧 담당 역할

- Jetson Orin Nano 기반 Edge Vision Pipeline 개발
- YOLO · PaddleOCR 모델 배포 및 추론 최적화
- PyTorch → TensorRT FP16 모델 변환
- Vision Model 비교 및 성능 평가
- MQTT 기반 AI Worker 구성
- Jenkins 기반 자동 배포 환경 구축

### 💡 Problem Solving

초기 시스템은 책장 한 칸을 처리하는 데 평균 **21.9초**가 소요되어  
실제 AIoT 서비스에 적용하기 어려운 문제가 있었습니다.

처음에는 모델 추론이 병목이라고 판단해  
YOLO 모델을 TensorRT FP16으로 변환했습니다.

- 책등 YOLO : `51.7ms → 25.8ms`
- 청구기호 YOLO : `40.4ms → 18.9ms`

하지만 전체 처리 시간은 개선되지 않았습니다.

End-To-End Pipeline을 단계별로 계측한 결과  
전체 시간의 약 65%가 요청마다 반복되는  
**Process · CUDA · OCR 초기화**에서 발생한다는 것을 확인했습니다.

이를 해결하기 위해 AI 모델을 요청마다 실행하는 구조에서  
**상주 GPU Worker 구조**로 변경했습니다.

### 🚀 Result

`21.9 sec → 1.93 sec`

**책장 한 칸 처리 시간을 약 10배 단축했습니다.**

### 🛠 Tech Stack

`Python` `PyTorch` `YOLO` `PaddleOCR` `OpenCV`  
`ONNX` `TensorRT` `CUDA` `Jetson Orin Nano`  
`MQTT` `Jenkins` `Linux`

---

## 📸 [CapShop](https://github.com/SyncShopper/syncshopper)

### 영상 속 상품을 캡처하면 AI가 유사 상품을 추천하는 서비스

유튜브 영상을 시청하다 마음에 드는 상품을 발견했을 때  
상품명을 직접 검색하지 않아도 화면 캡처만으로  
유사한 쇼핑 상품을 찾을 수 있도록 만든 서비스입니다.

### 🔧 담당 역할

- LangGraph 기반 상품 검색 · 추천 AI Pipeline 설계
- Gemini 기반 이미지 분석 및 상품 특징 추출
- OCR · Visual Analysis 병렬 처리
- 상품 특징 기반 검색 Query 생성
- Naver Shopping API 연동
- 검색 후보 Filtering 및 Visual Re-ranking
- FastAPI 기반 AI Server 개발
- Chrome Extension 캡처 기능 구현
- Spring Boot Backend와 AI Server 연동

### 💡 Problem Solving

초기 검색 Pipeline은 여러 단계에서 LLM을 호출하면서  
한 번의 상품 검색에 **50~100초 이상**이 소요되는 병목이 발생했습니다.

이를 해결하기 위해

- Query 생성 : `LLM 호출 → Keyword Rule 기반 처리`
- 독립적인 AI Node 병렬 실행
- LLM Timeout 및 Fallback 적용

방식으로 Pipeline을 개선했습니다.

### 🚀 Result

검색 Query 처리 시간을

`14 sec → 1 sec`

수준으로 단축하고,  
LLM 응답 지연이 발생하더라도 최대 검색 시간을 제한할 수 있도록 개선했습니다.

### 🛠 Tech Stack

`Java` `Spring Boot` `Spring Security` `MyBatis`  
`Python` `FastAPI` `LangGraph` `Gemini API`  
`Naver Search API` `MySQL` `Docker` `Chrome Extension`

---

## 🌱 Currently Learning

- LangGraph 기반 AI Agent 및 Workflow Architecture
- RAG · Text-to-SQL 검색 정확도 개선
- Multimodal Search & Recommendation
- AI Pipeline 성능 최적화
- Spring Boot Backend Architecture
- Docker · CI/CD 기반 서비스 운영

---

### AI 기술을 모델에서 끝내지 않고, 실제 서비스로 연결하겠습니다. 🚀

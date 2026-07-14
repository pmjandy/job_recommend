# 💼AI Job Recommendation System    

## 📌Project Overview
본 프로젝트는 사용자의 전공, MBTI, 오행 정보를 기반으로 적합한 직업을 추천하는 AI 기반 직업 추천 시스템입니다.    

커리어넷 openAPI를 통해 직업백과 데이터를 크롤링하였으며, SentenceTransformer를 이용하여 사용자 성향과 직업 정보를 동일한 임베딩 공간에 표현하여 의미적 유사도를 계산합니다. 또한 openAPI GPT를 활용하여 각 추천 직업에 대한 적합한 이유를 자연어로 제공합니다.


## 🎯Project Objectives
- 사용자의 개인적인 성향 및 기질을 반영한 개인 맞춤형 직업 추천
- 전공, 관심사 등 표면적인 정보는 물론 MBTI, 오행을 함꼐 고려한 추천 시스템 구현
- LLM을 이요한 추천 결과에 대한 이유 함께 제공


## 📊Data Collection
커리어넷 openAPI를 통해 직업백과 데이터 크롤링

### 수집항목
- 직업코드
- 직업명
- 직업분류
- 하는일
- 핵심능력
- 관련학과
- 적성
- 흥미
- 직업전망
- 업무환경
- 업무수행


## 🧹Data Preprocessing
- '하는일' 칼럼의 'work'키를 추출해 '주요업무'칼럼 생성
- 관련학과가 'nan'일 경우 '관련없음'으로 변경
- '적성'과 '흥미'칼럼을 결합해 '흥미적성'칼럼 생성
- '관련학과'의 항목들 중, 동일한 학과의 다양한 명칭을 하나로 정규화


## 🤖Recommendation Model
### User information
- 전공
- MBTI
- 오행

### Embedding Model
- SentenceTransformer
- jhgan/ko-sbert-multitask


## 💡Recommendation Process
User input(전공 + MBTI + 오행)  
↓  
전공 기반 직업 필터링(직업 벡터 생성)  
↓  
사용자 mbti/오행에 해당하는 문장 매핑(0.5, 0.5 가중합 -> 사용자 벡터 생성)  
↓  
직업 벡터와 사용자 벡터의 코사인 유사도 계산  
↓  
top3 직업 추천  
↓  
GPT 기반 추천 이유 생성


## 🛠️Tech Stack
### Language
- Python

### AI/NLP
- SentenceTransformer
- PyTorch
- OpenAI API

### Data
- pandas
- numpy

### Interface
- Gradio

### External API
- 커리어넷 openAPI

## 📷Demo
사용자는 다음의 정보를 입력합니다.
- 전공
- MBTI
- 오행

출력결과
- 추천 직업
- 유사도 점수
- 주요 업무
- 추천 이유


## 🚀Future Improvements
- 사용자 프로필 정교화(mbti 및 오행 특징 구체화)
- 추천된 직업에 적합한 커리어 로드맵 제안
- 실시간 채용정보 및 트렌드를 반영한 추천 시스템 구현
- 모델 자체적인 오행 계산 알고리즘 구현

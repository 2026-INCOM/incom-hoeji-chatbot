# incom-hoeji-chatbot

인하대 컴퓨터 동아리 **INCOM** 2학기 첫 수요모임(2026-09-23) 자료입니다.
회지(회칙 + 행사 후기)를 데이터로, 코랩 무료 T4 하나에서 **Unsloth LoRA 파인튜닝**과 **RAG**를 만들어 같은 질문으로 비교합니다.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/2026-INCOM/incom-hoeji-chatbot/blob/main/notebooks/incom_chatbot.ipynb)

## 구성

| 경로 | 내용 |
|---|---|
| `notebooks/incom_chatbot.ipynb` | 전처리 → QA 생성 → Unsloth 학습 → RAG → 비교, 코랩 T4용 |
| `data/hoeji_excerpt.docx` | 45기 회지 발췌본 (INCOM 회칙 + 45·46기 행사 후기). 회원 명부는 제외 |
| `data/qa_train.jsonl` | 회지 청크에서 LLM으로 생성한 학습용 QA 쌍 |
| `slides/incom_chatbot_session.pdf` | 세션 발표자료 |

## 실행

1. 위 배지로 코랩을 열고 **런타임 → 런타임 유형 변경 → T4 GPU**
2. 위에서부터 순서대로 실행. 설치 셀은 3~6분 걸립니다
3. 런타임을 재시작했다면 **런타임 → 이전 셀 모두 실행**

## 스택

- LLM: [unsloth/Qwen3.5-4B](https://huggingface.co/unsloth/Qwen3.5-4B) (4bit QLoRA, LoRA r=16)
- 학습: [Unsloth](https://github.com/unslothai/unsloth) + TRL SFTTrainer
- 임베딩: [Qwen/Qwen3-Embedding-0.6B](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B)
- 벡터 검색: FAISS (IndexFlatIP)

## 데이터 사용에 관해

회지 텍스트는 INCOM 내부 자료이며 동아리 교육 목적으로 공개합니다.

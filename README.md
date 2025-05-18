# 🧠 Kiosk Backend

AI 기반 어르신 음성인식 키오스크 프로젝트의 백엔드 서버입니다.  
사용자의 음성 입력을 STT → NLP → TTS 흐름으로 처리하여, 어르신도 쉽게 키오스크를 이용할 수 있도록 지원합니다.

---

## ⚙️ 기술 스택

- Python 3.10+
- FastAPI
- Uvicorn (ASGI 서버)
- Pydantic (데이터 모델링)
- Whisper (STT: 음성 → 텍스트)
- KoBERT (NLP: 의도 분석)
- Kakao TTS API (텍스트 → 음성 변환)
- GitHub Actions (버전 관리 및 협업)

---

## 🔧 주요 기능

| 기능 | 설명 |
|------|------|
| `/stt` | 사용자 음성 파일을 Whisper로 텍스트로 변환 |
| `/intent` | STT 결과 텍스트를 KoBERT로 분석하여 사용자 의도 분류 |
| `/response` | 의도에 따라 시나리오 응답 메시지 반환 |
| `/tts` | 응답 메시지를 TTS API로 변환하여 음성 URL 반환 |

> 위 API는 프론트엔드에서 키오스크 UI와 연동됩니다.

---

## 👨‍👩‍👧‍👦 팀원 및 역할

| 이름 | 역할 | 담당 내용 |
|------|------|-----------|
| 이예림 (팀장) | 백엔드 개발 | FastAPI 기반 API 서버 구현 및 AI 연동, 시스템 통합 |
| 김은서 | 프론트엔드 개발 | 키오스크 UI 제작 및 TTS 음성 응답 연동 |
| 이소영 | AI 모델 개발 | Whisper, KoBERT 기반 STT/NLP 모델 구성 및 실험 |

---

## 🚀 실행 방법

### 1. 가상 환경 설정
```bash
python -m venv venv
source venv/bin/activate  # Windows는 venv\Scripts\activate

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

---

## ▶️ 서비스 흐름

```plaintext
[사용자 음성 입력]
       ↓
[프론트엔드]
  - 마이크 녹음
  - 백엔드에 음성 파일 전송 (/process)
       ↓
[백엔드]
  - AI 서버에 음성(STT) → 텍스트
  - AI 서버에 텍스트 → Intent 분석
  - 분석된 Intent 기반 응답 메시지 생성
       ↓
[프론트엔드]
  - 응답 메시지를 TTS로 음성 재생
```

--

## 🔧 주요 기능

| 기능 |	메서드 | 설명 |
|------|------|------|
| `/process` | POST | 프론트에서 받은 음성 파일을 AI 서버(STT+Intent)로 보내고, 텍스트 및 의도를 종합해서 반환 |

> 위 API는 프론트엔드에서 키오스크 UI와 연동됩니다.

---

## 🏁 응답 예시

```json
{
  "text": "진료 예약하고 싶어요",
  "intent": "RESERVATION"
}
```

---

## 👨‍👩‍👧‍👦 팀원 및 역할

| 이름 | 역할 | 담당 내용 |
|------|------|-----------|
| 이예림 (팀장) | 백엔드 개발 | FastAPI 기반 REST API 서버 구축, 프론트와 AI 서버 간 연동 API 설계 및 구현 |
| 김은서 | 프론트엔드 개발 | 키오스크 UI 제작 및 TTS 음성 응답 연동 |
| 이소영 | AI 모델 개발 | 모델 추론 API 서버 구축 (/stt, /intent) |

---

## 🚀 실행 방법

### 1. 가상 환경 설정
```bash
python -m venv venv
source venv/bin/activate  # Windows는 venv\Scripts\activate

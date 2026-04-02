# 💠 Beans Pirates

**The Essence of Kinetic Intelligence**

우리는 복잡한 데이터 망을 조율하여 신체 움직임의 본질적인 진실을 찾아내는 고성능 기술 스택을 구축합니다.  

SAiM: B2C 형태의 AI 피트니스 코칭 시스템

SAiM Manager: 피트니스 조직의 CRM Tool

---

### 🚀 Core Focus
* **Kinetic Analysis:** 실시간 신경망 분석을 통한 정밀한 피트니스 가이드 및 데이터 기반 케어 솔루션 연구.
* **High-Performance Backend:** 대규모 데이터 처리를 위한 견고하고 확장 가능한 시스템 설계.
* **System Orchestration:** 복잡한 서비스 메시를 완벽하게 제어하는 프레임워크 및 인프라 최적화.

---

```mermaid
sequenceDiagram
    autonumber
    participant U as User
    participant FE as Frontend
    participant BE as Backend
    participant SP as Social Provider

    U->>FE: 소셜 로그인 버튼 클릭
    FE->>BE: GET /v1/oauth/{socialType}/authorize

    Note right of BE: state 생성 및 저장
    BE-->>FE: 302 Redirect (소셜 로그인 인가 URL)
    FE->>SP: 인가 페이지로 이동

    U->>SP: 로그인 및 동의 진행
    SP-->>BE: GET /v1/oauth/{socialType}/callback?code=...&state=...

    Note right of BE: state 검증
    Note right of BE: code로 provider access token 요청
    Note right of BE: 사용자 정보 조회
    Note right of BE: 회원 존재 여부 확인 및 필요 시 회원 생성
    Note right of BE: tempToken 발급

    BE-->>FE: 302 Redirect (프론트 redirect URI + tempToken)

    Note over FE: tempToken 추출
    FE->>BE: POST /v1/oauth/exchange
    Note left of BE: { tempToken }

    Note right of BE: tempToken 검증 및 consume
    Note right of BE: customer 조회
    Note right of BE: accessToken / refreshToken 발급
    Note right of BE: refreshToken 저장
    Note right of BE: onboardingCompleted 포함 응답

    BE-->>FE: 200 OK { accessToken, refreshToken, onboardingCompleted }

    alt onboardingCompleted == false
        Note over FE: accessToken / refreshToken 저장 후 온보딩 화면으로 이동
    else onboardingCompleted == true
        Note over FE: accessToken / refreshToken 저장 후 홈 화면으로 이동
    end

```

### 🌐 Contact & Collaboration

우리는 기술적 한계를 돌파하고, 기술로 미래를 구현합니다.

* **Website:** [beans-pirates.co.kr](https://beans-pirates.co.kr)
* **Location:** Korea, South

---
*Beans Pirates - Exploring the boundaries of movement and technology.*

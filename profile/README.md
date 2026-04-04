# 💠 Beans Pirates

**The Essence of Kinetic Intelligence**

우리는 복잡한 데이터 망을 조율하여 신체 움직임의 본질적인 진실을 찾아내는 고성능 기술 스택을 구축합니다.  

SAiM: B2C 형태의 AI 피트니스 코칭 시스템

SAiM Manager: 피트니스 조직의 CRM Tool

```mermaid
sequenceDiagram
    participant U as User
    participant C as Client
    participant P as Kakao/Naver
    participant S as Server
    participant D as DB

    U->>C: 소셜 로그인 버튼 클릭
    C->>P: 로그인 요청
    P-->>C: accessToken 발급

    C->>S: POST /v1/oauth/login
    Note over C,S: socialType + accessToken 전달

    S->>P: 사용자 정보 조회 요청
    Note over S,P: Authorization: Bearer accessToken
    P-->>S: providerUserId, email 등 사용자 정보 응답

    S->>D: SocialAccount 조회
    alt 기존 회원 존재
        D-->>S: 기존 회원 반환
    else 신규 회원
        S->>D: Customer 생성
        S->>D: SocialAccount 생성
        D-->>S: 신규 회원 반환
    end

    S->>S: 서비스 accessToken / refreshToken 발급
    S-->>C: 로그인 응답 반환
    Note over S,C: accessToken + refreshToken + onboardingCompleted
```
```mermaid
sequenceDiagram
    participant U as User
    participant C as Client
    participant G as Google
    participant S as Server
    participant D as DB

    U->>C: 구글 로그인 버튼 클릭
    C->>G: 구글 로그인 진행
    G-->>C: idToken 발급

    C->>S: POST /v1/oauth/login
    Note over C,S: socialType + idToken 전달

    S->>S: Google ID Token 검증
    Note over S: aud / iss / exp / 서명 검증
    S->>S: payload 추출
    Note over S: sub, email 등 사용자 정보 확보

    S->>D: SocialAccount 조회
    alt 기존 회원 존재
        D-->>S: 기존 회원 반환
    else 신규 회원
        S->>D: Customer 생성
        S->>D: SocialAccount 생성
        D-->>S: 신규 회원 반환
    end

    S->>S: 서비스 accessToken / refreshToken 발급
    S-->>C: 로그인 응답 반환
    Note over S,C: accessToken + refreshToken + onboardingCompleted
```



---

### 🚀 Core Focus
* **Kinetic Analysis:** 실시간 신경망 분석을 통한 정밀한 피트니스 가이드 및 데이터 기반 케어 솔루션 연구.
* **High-Performance Backend:** 대규모 데이터 처리를 위한 견고하고 확장 가능한 시스템 설계.
* **System Orchestration:** 복잡한 서비스 메시를 완벽하게 제어하는 프레임워크 및 인프라 최적화.

---

### 🌐 Contact & Collaboration

우리는 기술적 한계를 돌파하고, 기술로 미래를 구현합니다.

* **Website:** [beans-pirates.co.kr](https://beans-pirates.co.kr)
* **Location:** Korea, South

---
*Beans Pirates - Exploring the boundaries of movement and technology.*

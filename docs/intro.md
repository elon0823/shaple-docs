---
sidebar_position: 1
---

# About Shaple

:boom: Shaple 은 원하는 Business 요구사항에 맞는 기능을 매우 쉽게 구현할 수 있도록 해주는 Backend as a Service (BaaS) 플랫폼으로 [Supabase](https://supabase.com), [Pocketbase](https://pocketbase.io) 등으로 부터 영감을 받아 시작되었습니다.

:dart: Shaple 은 다음과 같은 개인 및 팀에서 사용하기 좋습니다.

- 👩‍💻 **개인**
  - Backend 개발 없이 서비스를 만들고자 하는 Frontend 개발자
  - Business 에 관련된 기능 개발에만 집중하고 Auth, Third party API 기능 등을 쉽고 빠르게 연동하고자 하는 Backend 개발자
  - 개발을 편하게 하고 싶은 모든 개발자
  - 개발 실력을 보완하여, 업무 완성도를 높이고 싶은 모든 개발자

- 👨‍👩‍👦‍👦 **팀**
  - 최소한의 개발 인력으로 IT 서비스/플랫폼 구축하고자 하는 기업 또는 팀
  - 빠르게 MVP 를 구현하거나 SI 프로젝트를 효율적으로 진행하고자 하는 기업 또는 팀

## 🧬 Design principles
- :memo: **Easy to use.**
  - Shaple 은 별도의 Learning curve 없이, 쉽게 사용할 수 있도록 설계되었습니다.
  - 서비스 요구사항을 입력하는 것만으로, 대부분의 Backend 기능을 구현할 수 있습니다.
- :hammer_and_wrench: **Easy to configure.**
  - Configuration 을 통해, 원하는 기능을 프로그래밍 없이 쉽게 구현할 수 있습니다.
  - 서비스 요구사항을 채팅 형태로 입력하는 것만으로, 필요한 configuration 을 쉽게 생성할 수 있습니다.
- :mag_right: **Easy to search.**
  - Shaple 챗봇을 통해 원하는 기능을 물어보고 위치를 쉽게 찾을 수 있습니다.
- :rocket: **Easy to deploy.**
  - Shaple 을 통해 구성한 Backend service 를 별도의 과정 없이 `Shaple-hosting` 을 통해 쉽게 배포할 수 있습니다.
  - `Shaple-hosting` 없이 K8s 기반의 MSA 환경을 쉽게 `self-hosting` 할 수 있도록 제공합니다.  

## 📦 Shaple Services
- 🔐 **Auth** :
  - Email, Phone, OAuth 등 다양한 인증 수단을 쉽게 사용할 수 있도록 제공합니다.
  - [Gotrue](https://github.com/netlify/gotrue) 를 확장하여 손쉬운 User 관리 및 인증 기능을 제공합니다.
- 🗄 **Storage**
  - Image, Video 등의 media 를 쉽게 관리하는 File storage 기능을 제공합니다.
  - S3 compatible API 를 지원합니다.
- 🗂 **Database**
  - [PostgreSQL](https://www.postgresql.org/) 를 사용하며 client SDK 를 통해 편리하게 db 에 접근하고 RLS(Row Level Security)를 통해 안전하게 데이터를 관리할 수 있습니다.
  - [Postgrest](https://postgrest.org/en/v7.0.0/) compatible API 를 지원합니다.
- 📝 **Functions**
  - TBD 
- ⏰ **Realtime**
  - TBD
- 🧩 **Vertical API extensions**
  - TBD

## ⚡ Chatbot Interface
shaple 은 자체 개발한 LLM 모델 기반으로 만든 Configuration chatbot을 통해 쉽게 원하는 기능을 포함하도록 프로젝트를 쉽게 구성할 수 있습니다.

사용자는 챗봇을 통해 서비스 기능을 자세히 설명하기만 하면, 챗봇이 요구사항을 분석하여 필요한 기능을 포함하는 Configuration 을 생성합니다.

### Use case
```
🤔 사용자 : "회원가입을 위해 Email 인증기능이 필요해요"
```
```
🤖 Shaplebot : "Email 인증 기능을 포함하도록 다음과 같은 configuration 을 구성하였습니다."
```
```toml
[api]
target = 'https://builder.shaple.io'

[auth]
[auth.external]
emailEnabled = true

[auth.smtp]
senderName = 'Shaple'
```
```
🤖 Shaplebot : "언제든지 위 configuration 으로 새로운 Shaple project 를 생성할 수 있습니다." 
               "추가로 필요한 기능이 있다면 알려주세요!" 
```
```
🤔 사용자 : "SMTP senderName 을 Shaple 에서 PAUST 로 변경해주세요. 그리고 회원가입시 SMS 인증도 필요해요."
```
```
🤖 Shaplebot : "다음과 같이 변경하였습니다."
```
```toml
[api]
target = 'https://builder.shaple.io'

[auth]
[auth.external]
emailEnabled = true
phoneEnabled = true

[auth.smtp]
senderName = 'PAUST'

[auth.sms]
provider = 'twilio_verify'

[auth.sms.twilioVerify]
AccountSID = {YOUR_TWILIO_ACCOUNT_SID}
AuthToken = {YOUR_TWILIO_AUTH_TOKEN}
MessageServiceSID = {YOUR_TWILIO_MESSAGE_SERVICE_SID}
```
```
🤖 Shaplebot : "twilio verify 를 provider 로 설정하는 가이드는 [이곳]을 참고하여 추후 수정 가능합니다."
```
```
🤔 사용자 : "위 내용으로 새로운 Shaple project 를 생성해주세요."
```
```
🤖 Shaplebot : "새로운 Shaple project [새로운 프로젝트1] 를 생성하였습니다. 이름은 언제든지 변경 가능합니다."
               
               Next step : "다음의 guide 를 참고하여 Shaple client SDK 를 통해 기능을 구현할 수 있습니다."
                           [Email 인증 기능 연동 Guide]
                           [SMS 인증 기능 연동 Guide] 
               
```

## Comparison with other tools

### Firebase

### Supabase

### Pocketbase

### Medusajs


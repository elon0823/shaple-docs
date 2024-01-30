---
sidebar_position: 4
---

# Configurations
Shaple 은 다양한 서비스를 쉽게 구성할 수 있도록 다양한 Configuration 을 제공합니다.

다음 예제와 같이 `shaple.toml` 파일에 각 서비스별로 필요한 설정을 추가하면, Shaple CLI 를 통해 쉽게 서비스를 구성할 수 있습니다.

```toml title="shaple.toml"
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
...
```

### Using environment variables
`SHAPLE_ENV` 를 통해 `shaple.dev.toml`, `shaple.toml` 파일을 구분합니다.

- `shaple stack update` : shaple.toml 파일을 사용합니다.
- `SHAPLE_ENV=dev shaple stack update` : shaple.dev.toml 파일을 사용합니다.


## 🔐Auth Configs
TBD

## 🗄Storage Configs
TBD

## 🗂Database Configs
TBD

## 📝Edge Functions Configs
TBD

## ⏰Realtime Configs
TBD

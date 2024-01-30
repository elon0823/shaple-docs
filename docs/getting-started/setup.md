---
sidebar_position: 1
---

# Setup Project using CLI

## Install Shaple CLI
1. Download [shaple-cli](https://github.com/paust-team/shaple-builder/releases/latest)
2. Add shaple-cli to your PATH
```bash
chmod +x shaple-cli
mv shaple-cli /usr/local/bin/shaple
```

## Create Project
```bash
shaple project create --project.name [project name]
```
`Project` refers to a unit that divides repositories or services in Shaple.

## Add Stack
```bash
shaple stack add -i [project id] --stack.name [stack name] --stack.siteURL [site url]
```
`Stack` is a unit divided within a `Project` and can be used in conjunction with branches.

## Get Stack Info
`shaple stack get -i <stack-id>` 를 통해 생성한 Stack 의 정보를 확인할 수 있습니다.

stack 에는 다음과 같은 정보가 포함되어 있습니다.
- `AnonApiKey`
  - 모든 사용자 API 를 사용하기 위한 API Key 입니다.
  - Admin API 를 사용할 수 없고 해당 public API 와 RLS 로 제한된 API 만 사용할 수 있습니다. 
- `AdminApiKey`
  - 모든 사용자 API 와 Admin API 를 사용하기 위한 API Key 입니다.
  - ❗️ _AdminApiKey 는 server-side 에서만 사용하는 것을 권장합니다._
- 기타 service configuration
  - ❗️ _service 를 enable 하기 전에는 stack info 에서 확인할 수 없습니다._ 

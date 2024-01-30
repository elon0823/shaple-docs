---
sidebar_position: 2
---

# Configure Services
여기서는 Shaple CLI 를 통해 간단히 Service를 구성하는 방법을 설명합니다. 

CLI 를 통해서 [setup](./setup.md#get-stack-info)에서 생성한 stack 에 각 service 를 enable/disable 할 수 있습니다.

## Configure Auth Service
- enable
    ```bash
    shaple stack auth enable -i [stack id]
    ```
- disable
    ```bash
    shaple stack auth disable -i [stack id]
    ```

### Configure
[shaple.toml] 파일을 통해 auth service 를 구성할 수 있습니다.

자세한 내용은 [auth configuration](/docs/configurations#auth-configs) 를 참고하세요.


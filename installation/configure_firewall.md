# [Accessible Guide For Machbase](../README.md) - 설치

## 설치 카테고리 목차

1. [Machbase 설치하기](./install.md)
2. **방화벽 설정하기**

## 목차

- [Accessible Guide For Machbase - 설치](#accessible-guide-for-machbase---설치)
  - [설치 카테고리 목차](#설치-카테고리-목차)
  - [목차](#목차)
  - [방화벽 설정 개요](#방화벽-설정-개요)
  - [명령어를 통한 방화벽 설정](#명령어를-통한-방화벽-설정)
    - [명령어](#명령어)

## 방화벽 설정 개요

Linux 가이드에선 Machbase 설치 이전에 해당 프로그램이 사용할 [포트를 미리 설정](https://machbase.atlassian.net/wiki/spaces/M7M/pages/417759521/Linux)합니다.

이와 비교해서 Windows 가이드는 Machbase를 설치한 이후 [방화벽 UI를 통해](https://machbase.atlassian.net/wiki/spaces/M7M/pages/417759721/Windows) 해당 프로그램이 사용할 포트를 설정하게 됩니다.

이 문서에서는 Windows에서 UI를 통한 방법 대신 Linux 가이드처럼 명령어로 방화벽의 설정을 변경하는 방법에 대해 다룰 것입니다.

## 명령어를 통한 방화벽 설정

명령 프롬프트에서 방화벽의 설정은 [`netsh`](https://learn.microsoft.com/en-us/windows-server/networking/technologies/netsh/netsh) 명령어를 통해 이루어집니다.

Machbase는 **5656, 5001 포트를 사용**합니다.

아래는 방화벽에서 해당 포트를 허용하기 위한 규칙을 추가하는 명령어입니다.

### 명령어

```sh
netsh advfirewall firewall add rule name="Machbase" description="Machbase Open Ports" dir=in protocol=TCP localport=5656,5001 action=allow profile=any
```

> ⚠ 명령어를 실행하는 데에 관리자 권한이 필요할 수 있습니다.

[[1]](./install.md) **\[2\]**

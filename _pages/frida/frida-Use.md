---
layout: single
title: "frida 사용법"
permalink: /frida/frida-Use/
sidebar:
  nav: docs
toc: true
toc_sticky: true
---

# 1. Frida 프로세스 연결 방식

## 1) Attach 방식
개념
- 이미 실행 중인 프로세스(앱)에 붙는 방식
- 디버거가 현재 실행 중인 앱을 중간에 잡아서 후킹하는 것과 유사
- 앱이 이미 실행 중이어야 하며, 앱의 초기 실행 로직(예 : `onCreate`, 초기 로딩 코드 등)은 이미 지나간 상태

장점
- 앱을 껏다 켜지 않아도 바로 후킹 가능
- 동작 중인 앱의 특정 부분을 번석할 때 유용
- 빠르게 attach해서 동적 상태를 확인 가능

단점
- 앱 실행 초반의 초기화 로직 (`Application.onCreate(), SSL Pinning 초기 로드 등)은 이미 지나가서 후킹 불가
- 일부 앱은 attach 시점에 anti-debugging 감지 코드를 실행할 수 있다

명령어 예시
```
frida -U -n com.example.app

frida -U -p 12345
```


## 2) Spawn 방식
개념
- 앱을 새로 실행시키면서 처음부터 후킹하는 방식

장점
- 앱 실행 초기부터 후킹 가능 (Application, MainActivity 초기화 등 포함)
- SSL Pinning, Root Check 등 초기화 시점에 걸린 보안 로직 우회에 유리
- anti-attach 감지 로직을 피할 수 있음

단점
- 앱을 다시 실행시켜야 함 (기존 실행 중이면 종료됨)
- attach보다 약간 느림 (프로세스 생성+스크립트 주입 과정이 있음)

명령어 예시
```
frida -U -f com.example.app
```

실제로 코드를 주입하고 실행하려면 `--no-pause` 옵션 추가
```
frida -U -f com.example.app -l script.js --no-pause
```
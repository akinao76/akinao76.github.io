---
layout: single
title: "frida 설치(Android)"
permalink: /frida/install_guide/
sidebar:
  nav: docs
toc: true
toc_sticky: true
---

# 1. Frida 설치
요구 사항
- Python 3.x version
- windows, macOS, Linux

파이썬 설치 확인
```
py --version
```

## 1) Frida Client 설치

```
# pip 최신화
pip install --upgrade pip

# frida-tools 10.x version + frida 16.7.19 설치
pip install --no-cache-dir "frida==16.7.19" "frida-tools>=12,<14"

#설치후 버전 확인
python -c "import frida; print(frida.__version__)"
```

## 2) Frida Server 설치

사전 작업
- Android 루팅
- adb 설치

Frida Server 다운로드
-> https://github.com/frida/frida/releases



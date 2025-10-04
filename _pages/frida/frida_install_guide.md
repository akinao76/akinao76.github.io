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

Frida Server 다운로드
-> https://github.com/frida/frida/releases


## 3) Frida Server 실행

사전 작업
- Android 루팅
- adb 설치

### Frida Server 파일 이동
```
adb push [Frida Server 파일 위치] /data/local/tmp
```

### Frida Server 설정
```
adb shell
cd /data/local/tmp
mv [Frida Server 이름] frida-server
chmod 755 frida-server
```

### Frida Server 실행

```
./frida-server &
```

# 2. Frida 명령어 테스트
설치된 애플리케이션 리스트를 볼 수 있는 'frida-ps' 명령어를 통해 정상적으로 구동되는지 확인

```
frida-ps -Uai
```


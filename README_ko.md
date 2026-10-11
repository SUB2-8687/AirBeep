# AirBeep

> 🌍 **Languages:** [English](./README.md) | [简体中文](./README_zh-CN.md) | 한국어

AirBeep은 iOS에 내장된 통화 녹음 안내음을 무음 처리하는 유틸리티입니다. 스위치 하나로 시작음과 종료음을 같은 길이의 무음으로 교체할 수 있고, 다시 끄면 자동 백업된 원본 파일로 복원됩니다.


## 기능

- 스위치 하나로 통화 녹음 시작음과 종료음을 무음 처리합니다.
- 처음 변경하기 전에 원본 안내음 파일을 자동으로 백업하며, 백업본은 유지되고 덮어쓰이지 않습니다.
- 파일을 쓸 때마다 다시 읽어서 검증합니다.
- 로컬 백업에서 한 번에 복원할 수 있습니다.
- 영어, 중국어 간체, 한국어 UI를 지원합니다.

## 작동 방식

AirBeep은 다음 시스템 파일에 대해 범위가 제한된 컨테이너 접근을 요청합니다.

- `/var/mobile/Library/CallServices/Greetings/default/StartDisclosureWithTone.m4a`
- `/var/mobile/Library/CallServices/Greetings/default/StopDisclosure.caf`

교체용 파일은 AirliftSilence의 무음 에셋을 기반으로 하며 원본과 같은 재생 시간을 유지합니다. 백업은 앱의 Documents 디렉터리 아래 `AirBeepBackups`에 저장됩니다.

## 요구 사항

- 지원되는 iOS/iPadOS 버전을 실행하는 실제 iPhone 또는 iPad:
  - **iOS/iPadOS 27.0 – 27.2 B2**
- 로컬 빌드에는 Xcode 27 이상이 필요합니다.
- 제공된 GitHub Actions 워크플로로 클라우드에서 서명되지 않은 IPA를 빌드할 수 있습니다.

> AirBeep은 비공개 시스템 동작에 의존하므로 iOS 버전에 따라 호환성이 달라질 수 있습니다. 녹음 안내음을 제거하면 상대방이 통화가 녹음되고 있다는 사실을 알 수 있는지 여부에 영향을 줄 수 있습니다. 현지 법률이 허용하고 필요한 동의를 받은 경우에만 사용하세요.

## 빌드

`airbeep.xcodeproj`를 열고 `airbeep` 타깃을 선택한 뒤 서명 팀을 설정하고 실제 기기로 빌드하세요.

서명되지 않은 IPA는 GitHub Actions에서 `Release unsigned IPA` 워크플로를 실행하면 됩니다. 결과물 이름은 `airbeep-v<version>-unsigned.ipa`입니다.

## 크레딧

- 무음 에셋과 교체 방식 연구: [AirliftSilence](https://github.com/YiHoooong/AirliftSilence)
- 프로젝트 의존성에 포함된 AirTraffic 및 Airlock 연구: 0xjohnny의 [airlift](https://github.com/0xjohnnydev/airlift)
- 원본 iOS 프로젝트 구조와 컨테이너 접근 구현: [Placard](https://github.com/frs0n/placard) 기여자 여러분

## 라이선스

AirBeep은 [GNU General Public License v3.0](LICENSE)으로 배포됩니다.

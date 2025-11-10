# Fire Detection Module

Python 기반의 실시간 화재(불꽃) 감지 모듈입니다.  
카메라 입력을 받아 불꽃을 탐지하고, MJPEG 스트리밍과 TCP 메시지 전송을 함께 처리합니다.  
모든 기능은 `mjpeg_server.py` 하나를 실행하면 자동으로 동작하도록 구성되어 있습니다.

## 주요 기능
- MobileNetV3 기반 화염 감지 모델(.pt) 로딩
- 카메라 실시간 프레임 처리
- MJPEG 스트리밍 자동 생성
- 불꽃 감지 시 TCP 메시지 자동 전송
- 단일 실행 스크립트로 전체 기능 통합

## 개발 목적
- Python·OpenCV 기반 영상처리 학습
- 딥러닝 모델(.pt) 추론 로직 구현
- MJPEG / TCP 통합 구조 설계 경험 축적

## 파일 설명
- `mjpeg_server.py` : 모든 기능을 통합하는 메인 실행 파일
- `camera_flame_yolov8_redsafe.py` : 감지 파이프라인 구성
- `detector_bridge.py` : 모델 로딩 및 불꽃 탐지 처리
- `common_utils.py`, `red_utils.py` : 영상 처리 및 공통 함수
- `flame_mobilenetv3_small.pt`  
- `flame_mobilenetv3_small_rebalanced.pt`  
  (화재 감지용 MobileNetV3 모델)

## 실행 환경
- OS : Ubuntu 24 LTS
- Python 3.10
- OpenCV, PyTorch, Numpy 등 사용

Linux 환경에서 가장 안정적으로 동작합니다.  
Windows에서도 실행 가능하지만 카메라/인코딩 환경에 따라 출력이 다를 수 있습니다.

## 실행 방법

### 단일 실행
아래 명령어 하나로 감지, 스트리밍, TCP 전송이 모두 동작합니다:
```bash
python mjpeg_server.py
```
- 자동으로 카메라를 열고  
- 자동으로 모델(.pt)을 로딩하며  
- 자동으로 MJPEG 스트림을 제공하고  
- 자동으로 감지 결과를 TCP로 전송합니다.

별도 실행 스크립트나 추가 명령이 필요하지 않습니다.



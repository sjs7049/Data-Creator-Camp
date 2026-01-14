# 환경 오염원 탐지 및 규모 추정 프로젝트
> **데이터 크리에이터 캠프 참여 프로젝트**

본 프로젝트는 딥러닝 모델을 활용하여 대기 오염원(굴뚝)을 자동으로 탐지하고, 이미지 기반으로 그 규모(높이)를 추정하는 엔드투엔드(End-to-End) 파이프라인 구축을 목표로 합니다.

## 주요 미션 및 해결 방안

### [Mission 1] 오염원 첫 발견 - 굴뚝 위치 탐지 (Object Detection)
- **목표:** 이미지 내 굴뚝의 위치를 정확하게 식별
- **모델:** `YOLOv8m` (Ultralytics)
- **주요 작업:** - JSON 형태의 라벨 데이터를 YOLO 포맷으로 변환하는 전처리 스크립트 작성
  - 데이터셋 분할 및 Augmentation을 통한 모델 강건성 확보
  - A100 GPU 환경 최적화 학습 진행 및 성능 평가

### [Mission 2] 배출 규모 가늠하기 - 굴뚝 높이 추정 (Regression)
- **목표:** 탐지된 오염원의 이미지를 바탕으로 실제 높이(m) 추정
- **모델:** `EfficientNet-B0` (Pre-trained) 기반 회귀 모델
- **주요 작업:**
  - 이미지 리사이징 및 정규화 파이프라인 구축
  - 높이 데이터(Target) 분포 분석 및 회귀 손실 함수(MSE) 적용
  - 학습 곡선(Loss Curve) 시각화를 통한 과적합 방지 및 성능 튜닝

## 기술 스택
- **Language:** Python 3.12+
- **Deep Learning:** PyTorch, Ultralytics(YOLOv8), Torchvision(EfficientNet-B0)
- **Environment:** Google Colab (A100 GPU)
- **Data Analysis:** Pandas, Matplotlib, OpenCV

---
**작성자:** 인하오남매
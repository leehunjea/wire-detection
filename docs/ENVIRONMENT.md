# 실행 환경 메모

원본 코드의 import를 읽어 확인한 의존성 목록입니다. 실제 동작하는 통합 환경이나 버전 잠금 파일을 복원한 것은 아닙니다.

| 용도 | 코드에서 확인한 라이브러리 |
|---|---|
| 공통 영상·수치 처리 | OpenCV (`cv2`), NumPy, Pillow, scikit-image |
| 그래프·표 | Matplotlib, pandas, seaborn, openpyxl, tabulate |
| 딥러닝 | PyTorch, torchvision, 일부 TensorFlow/Keras 실험 |
| 검출·분할 | Ultralytics, Detectron2, MMDetection, MMEngine, Matterport Mask R-CNN |
| 평가·설정 | pycocotools, PyYAML |
| 추적 참고 코드 | `sort` 모듈. 이 자료만으로 해당 로컬 모듈의 재현 환경은 확인되지 않음 |

## 사용할 때

1. 목적에 맞는 노트북 하나를 선택합니다. 서로 다른 프레임워크 실험은 환경을 따로 준비하는 것이 좋습니다.
2. 노트북의 이미지·데이터셋·모델 절대경로를 현재 보관 위치로 바꿉니다. 경로 안내는 [DATA_AND_MODELS.md](DATA_AND_MODELS.md)를 참고합니다.
3. `local_archive/frameworks`에 보존한 당시 소스의 설치 정보와 선택한 노트북의 import를 확인하여 환경을 구성합니다. 프레임워크 소스에 연구 중 수정한 코드가 포함됐을 수 있습니다.
4. 입력 한 쌍에 대한 추론부터 확인한 뒤 필요한 셀을 실행합니다. 설치·다운로드·학습·파일 저장 셀은 내용을 확인한 뒤 실행합니다.

`scripts/feature_matching`과 `scripts/baselines`의 Python 파일은 `Test*.jpg`를 **현재 작업 디렉터리**에서 읽습니다. 스크립트 파일의 위치를 기준으로 찾는 것이 아닙니다. 필요한 이미지를 작업 디렉터리에 준비하거나 코드의 입력 경로를 지정해야 합니다. 원본 이미지와 이전 폴더는 로컬 아카이브의 `legacy/Sift 알고리즘`에 보관되어 있습니다. [스크립트별 입력과 역할](../scripts/README.md)

노트북의 폴더는 탐색을 위한 분류입니다. 파일을 연 위치를 실행 환경으로 가정하지 마세요. MMDetection 실험의 `configs/`, 초기 Mask R-CNN 실험의 `../`와 `samples/coco` 등은 외부 프레임워크 배치와 작업 디렉터리에 의존합니다. 폴더 정리로 이 실행 조건이 자동 구성되는 것은 아닙니다.

## English notes

Notebook contents and Python script bytes are unchanged by the folder reorganization. Configure each experiment's data, weight, framework, and working-directory paths before running it. The feature-matching and YOLOv5 scripts read Test*.jpg from the **current working directory**, not from their own script folder. MMDetection configs and the legacy Mask R-CNN paths depend on external framework layouts.

정리 과정에서는 연구 코드를 실행하지 않았으며 모델 정확도, 학습 재개, GPU/CUDA 호환성을 검증하지 않았습니다. 파일 무결성, 노트북 JSON 구조, 공개용 사본의 소스 보존, 저장 출력 제거 및 패키지 용량을 확인했습니다.

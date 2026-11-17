# 코드 구성 안내

연구 노트북 21개와 Python 스크립트 5개를 목적별로 분류했습니다. 파일 이름의 공백·특수문자·원본 프레임워크 폴더 접두사를 정리했으며, 코드 내용은 그대로 보존했습니다.

## 노트북

| 폴더 | 파일 수 | 내용 |
|---|---:|---|
| [change_detection](../notebooks/change_detection/) | 4 | YOLO와 2DCNN, 배전공가 변화·이상 탐지 관련 실험 |
| [change_detection/variants](../notebooks/change_detection/variants/) | 3 | 영상 비교의 다른 실험 버전 |
| [model_experiments/yolo](../notebooks/model_experiments/yolo/) | 5 | YOLOv8·v9·v11 관련 학습·분할·저장 실험 |
| [model_experiments/other_detectors](../notebooks/model_experiments/other_detectors/) | 4 | Mask R-CNN/FPN, ConvNeXt, RTMDet, RT-DETR 비교 |
| [analysis](../notebooks/analysis/) | 2 | 모델 비교 그래프와 영상 전처리 |
| [legacy](../notebooks/legacy/) | 3 | 초기 Mask R-CNN, SORT, 다른 주제의 YOLOv8 참고 실험 |

### 먼저 볼 파일

1. [YOLOv11 + 2DCNN](../notebooks/change_detection/yolov11_2dcnn.ipynb): 여러 영상 비교 방식과 모델을 조합한 연구
2. [이상 탐지](../notebooks/change_detection/anomaly_detection.ipynb): 영상 간 변화·이상 탐지 관련 실험
3. [YOLO 계열 실험](../notebooks/model_experiments/yolo/yolov11_experiments.ipynb): YOLOv11을 비롯한 여러 YOLO 버전의 실험 셀
4. [모델 비교 그래프](../notebooks/analysis/model_comparison.ipynb): 논문 성능 표와 대조한 저장 수치 및 그래프 코드

variants는 서로 다른 실험 사본을 보존한 폴더입니다. 파일의 번호나 이름을 성능 순위·최종 모델 선정으로 해석하지 않습니다. 논문과 코드의 대응 범위는 [논문 안내](PAPER.md)에 기록했습니다.

## Python 스크립트

| 폴더 | 파일 수 | 내용 |
|---|---:|---|
| [feature_matching](../scripts/feature_matching/) | 4 | ORB, SIFT+BF, SIFT+FLANN, SIFT 기반 영상 비교 |
| [baselines](../scripts/baselines/) | 1 | YOLOv5의 검출 결과와 영상 차이를 이용한 변화 탐지 |

이전 이름 YOLOv5+sift.py에는 실제 SIFT 호출이 없어 현재는 yolov5_change_detection.py로 표기합니다. [스크립트별 입력 안내](../scripts/README.md)

## 실행 경로

폴더는 자료 탐색을 위한 분류입니다. 선택한 노트북의 데이터·가중치·외부 프레임워크 경로와 작업 디렉터리를 확인한 뒤 실행해야 합니다. SIFT/ORB와 YOLOv5 스크립트의 Test*.jpg 입력은 현재 작업 디렉터리 기준입니다. [환경 안내](ENVIRONMENT.md) · [로컬 자료 안내](DATA_AND_MODELS.md)

## 이동 기록과 검증

[FILE_PROVENANCE.csv](FILE_PROVENANCE.csv)에 원본 위치, 로컬 보관 위치, 이전 공개 경로, 현재 공개 경로와 SHA-256을 기록했습니다. 같은 공개 노트북에 대응하는 중복 원본 행도 보존했습니다.

이번 폴더 정리에서 **노트북 21개와 Python 파일 5개는 바이트 단위로 동일**하며, 대표 이미지 3개도 그대로 유지했습니다. 노트북 JSON과 출력 제거 상태, Python 구문, 문서 링크를 확인했습니다. 학습·추론은 다시 실행하지 않았습니다.

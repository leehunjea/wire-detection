# 로컬 자료 보관 안내

GitHub 정리본에는 원본 데이터와 가중치를 포함하지 않습니다. 아래 경로는 `github`와 나란히 있는 `local_archive` 기준입니다. 새 PC에서 사용할 때에는 필요한 자료를 별도로 복사한 뒤 노트북 경로를 수정해야 합니다.

| 경로 | 자료 |
|---|---|
| `data/캡스톤 데이터` | 수집한 원본 이미지. 바이트가 동일한 중복 사본만 삭제하고 대표 사본 보존 |
| `data/Wire`, `data/Wire2` | 전선 검출/세그멘테이션 데이터와 라벨 |
| `data/json dataset`, `data/coco-segmentation` | COCO 내보내기 자료. 이미지와 실질 라벨이 같지만 메타데이터가 달라 각각 보존 |
| `data/YOLOv8 test.v4i.coco` | 다른 학습·검증·시험 분할의 COCO 데이터 |
| `data/DOTAv1` | 항공영상 및 라벨 참고 데이터 |
| `data/None Labeling캡스톤 데이터`, `data/wireod` | 라벨링 전 이미지 및 시험 이미지 |
| `models/Wire` | 별도 저장된 학습 모델 4개 |
| `results/training/YOLOv11/runs` | YOLOv11 계열 실험의 가중치·설정·지표 |
| `results/training/ultralytics-main/runs` | YOLOv8 계열 실험의 가중치·설정·지표 |
| `results/training/yolov9-main/runs` | YOLOv9 실험 결과 |
| `results/training/detectron2-main/output` | Detectron2 최종 모델과 평가 결과 |
| `results/training/mmdetection-main/work_dirs` | ConvNeXt 등 실험별 체크포인트·로그 |
| `frameworks` | 당시 사용한 프레임워크 소스, 사전학습 가중치, 원본 라이선스 |
| `notebooks` | 최상위에 있던 원본 노트북. 기존 실행 출력 포함 |
| `results/figures`, `results/change_detection` | 저장된 시각화와 변화 탐지 실험 |
| `audit` | 전체 파일 이동 내역, 삭제 목록, 검증 결과 |

번호가 붙은 YOLO 중간 체크포인트 19개는 사용자 승인 후 삭제했습니다. 각 실험의 `best.pt`, `last.pt`, 로그와 지표는 해당 학습 결과 폴더에 보존했습니다. 삭제된 중간 시점의 optimizer 상태로 학습을 재개할 수는 없습니다.

원래의 폴더 경로에서 새 보관 경로로의 정확한 대응은 `local_archive/audit/file-moves.csv`에서 확인할 수 있습니다. 노트북에 남아 있는 과거 C: 드라이브 경로는 이번 폴더 이동 이전부터 존재한 경로입니다.

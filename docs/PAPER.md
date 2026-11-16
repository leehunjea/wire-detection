# 논문과 연구 코드 안내

## 서지정보

- 제목: **딥러닝 기반 객체 탐지를 활용한 배전공가 이상 탐지 모델 연구**
- 저자: 이훈제, 김진성, 정세훈, 심춘보
- 학술지: 스마트미디어저널 (Smart Media Journal), 14권 8호, 60–72쪽
- 발행: 2025년 8월
- DOI: [10.30693/SMJ.2025.14.8.60](https://doi.org/10.30693/SMJ.2025.14.8.60)
- 확인 출처: [KCI 논문정보](https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART003234567)

## 관련 코드를 찾는 순서

아래 대응은 KCI 초록의 연구 구성과 보관된 코드의 이름·import·모델 설정을 대조한 안내입니다. 논문 본문의 모든 실험과 체크포인트를 일대일로 확정한 재현 목록은 아닙니다.

| 관심 내용 | 관련 파일 | 코드에서 확인한 내용 |
|---|---|---|
| 2DCNN과 검출·분할 모델을 이용한 영상 비교 | [2DCNN+YOLOv11](../notebooks/research/2DCNN%2BYOLOv11.ipynb) | `Simple2DCNN`, `nn.Conv2d`, 모델 가중치를 이용한 여러 실험 셀 |
| YOLOv11 세그멘테이션 실험 | [YOLOv11](../notebooks/experiments/YOLOv11.ipynb) | `YOLO('yolo11l-seg.pt')` 로딩과 관련 실험 |
| 배전공가 변화·이상 탐지 | [모델 이상 탐지](../notebooks/research/모델%20이상%20탐지.ipynb) | 영상 비교와 CNN 관련 실험 |
| Mask R-CNN 계열 비교 | [Detectron2 실험](../notebooks/experiments/detectron2-main__detectron2.ipynb) | ResNet/FPN 백본 설정 |
| ConvNeXt 계열 비교 | [MaskRCNN+ConvNeXT](../notebooks/experiments/mmdetection-main__MaskRCNN%2BConvNeXT.ipynb) | ConvNeXt 체크포인트와 대체 설정을 포함한 실험 |
| 모델 비교 그래프 | [chart](../notebooks/analysis/chart.ipynb) | 초록에 등장하는 비교 모델 이름과 그래프 생성 코드 |

`chart.ipynb`의 수치는 원본 코드에 기록된 값입니다. 논문 최종 표와의 일치 여부를 확인하거나 실험을 다시 실행하지 않았으므로, README에 검증된 논문 성능으로 옮기지 않았습니다. RT-DETR·RTMDet·SIFT·초기 실험도 함께 보존되어 있습니다.

## 인용

저장소 루트의 [CITATION.cff](../CITATION.cff)는 학술지 논문을 `preferred-citation`으로 지정했습니다. [CITATION.bib](../CITATION.bib)도 함께 제공합니다. 저자 표기는 KCI의 국문 서지정보를 따릅니다. 논문 DOI를 소프트웨어 자체의 DOI로 표기하지 않았습니다.

## PDF 공개 범위

확인일: **2026-11-16**.

[학술지 저작권 안내 시스템(KJCI)](https://copyright.oak.go.kr/search/copyInfo.do?jourCopySeq=2468)은 저작권자를 한국스마트미디어학회로 안내하며, CC 라이선스와 셀프아카이빙 정책이 등록되어 있지 않다고 표시합니다. 해당 정책 페이지의 최종 수정일은 **2021-04-05**입니다.

[학회 논문투고규정](https://kism.or.kr/bbs/content.php?co_id=NO02010000)의 제11조도 게재 승인 이후 저작권의 학회 귀속과 저작권 위임서 제출을 안내합니다. 확인된 규정의 최신 개정일은 **2023-05-25**입니다.

이 정보만으로 GitHub에 발행 PDF를 재배포할 권한을 확인할 수 없어, 공개 패키지에는 서지정보와 공식 접근 링크를 포함했습니다. PDF 내부의 개별 라이선스나 저자와 학회 사이의 별도 계약은 확인하지 못했습니다. 재배포를 허용하는 별도 근거가 확인되면 해당 조건에 맞는 버전을 추가할 수 있습니다.

위 정책 설명은 논문 PDF에 관한 것이며, 코드에 새 라이선스를 부여하지 않습니다.

# Wire Detection & Change Analysis

배전공가의 전선·전주 영상에서 구조적 변화와 이상을 탐지하는 연구 자료입니다. 아래 KCI 등재 논문과 관련된 모델별 실험 노트북, 영상 비교 코드, 대표 시각화 결과를 정리했습니다.

## 관련 논문

**이훈제, 김진성, 정세훈, 심춘보. (2025). 딥러닝 기반 객체 탐지를 활용한 배전공가 이상 탐지 모델 연구. 스마트미디어저널, 14(8), 60–72.**

[DOI: 10.30693/SMJ.2025.14.8.60](https://doi.org/10.30693/SMJ.2025.14.8.60) · [KCI 논문정보](https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART003234567) · [BibTeX](CITATION.bib)

논문은 **YOLOv11l-seg와 2DCNN을 결합한 배전공가 이상 탐지**를 다룹니다. 세그멘테이션 레이블링과 데이터 증강을 적용하고, YOLOv8l-seg·YOLOv9c-seg·Mask R-CNN 계열·ConvNeXt 등과 비교했습니다. 위 설명은 KCI에 등록된 초록을 요약한 것입니다.

[논문과 코드 안내](docs/PAPER.md)에서 관련 노트북과 확인 범위를 볼 수 있습니다. 인용할 때는 [CITATION.cff](CITATION.cff)의 논문 정보를 사용할 수 있습니다. PDF 파일은 재배포 허용 범위가 확인되지 않아 포함하지 않았으며, 원문은 DOI 또는 KCI 링크에서 확인할 수 있습니다.

## 연구 내용

- YOLOv8 / YOLOv11 / YOLOv9, RT-DETR, Detectron2, Mask R-CNN + ConvNeXt, RTMDet 관련 실험
- 전선·전주 영역을 이용한 영상 간 변화 및 이상 탐지
- SIFT 특징점, 영상 차이, 거리 기반 비교와 시각화
- 모델 비교 그래프 및 결과 정리

파일에 남아 있는 여러 실험 버전을 보존한 연구 아카이브입니다. 논문과 개별 체크포인트의 최종 대응 관계 및 성능 수치 재현은 아직 검증하지 않았습니다.

## 구성

```text
notebooks/
  research/       전선·전주 변화 및 이상 탐지
  experiments/    모델별 학습·추론 실험
  analysis/       그래프와 영상 전처리
  legacy/         초기 실험·템플릿·다른 주제의 참고 실험
src/sift/         SIFT 비교 스크립트
results/representative/  원본에서 선별한 대표 결과 이미지
docs/             데이터·모델 위치, 실행 환경 및 파일 출처 안내
```

## 먼저 볼 파일

| 파일 | 내용 |
|---|---|
| [모델 이상 탐지](notebooks/research/모델%20이상%20탐지.ipynb) | 전선·전주 변화 및 이상 탐지 실험 |
| [Wire detection good](notebooks/research/Wire%20detection%20good.ipynb) | 전선 세그멘테이션과 영상 비교 |
| [2DCNN + YOLOv11](notebooks/research/2DCNN%2BYOLOv11.ipynb) | 여러 영상 비교 방법과 모델을 조합한 실험 |
| [chart](notebooks/analysis/chart.ipynb) | 모델 비교·보고용 그래프 |

파일 이름의 `good`, `success`는 원본 명칭이며 최종 성능 검증을 뜻하지 않습니다.

## 대표 결과

### 비교 방법별 시각화

![비교 방법별 전선 변화 시각화](results/representative/methods_comparison.jpg)

### 변화 영역 탐지 사례

![추가된 영역의 탐지 사례](results/representative/change_detection_success.png)

이미지는 기존 실험에서 저장한 출력입니다. 이미지에 표시된 변화율은 해당 사례의 출력값이며 전체 데이터셋의 정확도나 성능 지표가 아닙니다. 원본 출처는 [대표 결과 안내](results/representative/README.md)에 기록했습니다.

## 실행 상태

이 저장소는 연구 자료 공개를 위한 정리본입니다. 노트북의 코드 셀은 원본 그대로이며, 저장된 실행 출력과 실행 번호는 제거했습니다. 동일한 코드 셀로 구성된 사본 하나는 합쳤습니다.

노트북에 과거 PC의 절대경로와 실험별 설정이 남아 있으므로, **그대로 전체 실행할 수 있는 통합 실행 패키지는 아닙니다.** 사용할 노트북의 데이터·가중치 경로를 먼저 설정하고 해당 모델 환경을 준비해야 합니다. 정리 과정에서는 모델 학습이나 추론을 실행하지 않았습니다.

- [데이터·모델 보관 위치](docs/DATA_AND_MODELS.md)
- [환경 및 실행 안내](docs/ENVIRONMENT.md)
- [원본 파일 대응표](docs/FILE_PROVENANCE.csv)

## 포함하지 않은 자료

원본 데이터, 학습 가중치, 전체 학습 로그, 외부 프레임워크 소스 및 원본 노트북 출력은 `github` 폴더와 나란한 `local_archive`에 보관했습니다. `.gitignore`에도 대용량 모델·데이터와 캐시 제외 규칙을 넣었습니다.

GitHub에 올릴 대상은 **이 README가 들어 있는 `github` 폴더의 내용**입니다. 전체 연구 폴더를 업로드하지 않습니다.

외부 프레임워크의 원본 라이선스는 로컬 보관본에 유지했습니다. 이 정리 과정에서 연구 코드에 새 라이선스를 임의로 부여하지 않았습니다.

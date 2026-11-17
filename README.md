# 배전공가 이상 탐지

**한국어** | [English](README.en.md)

**Wire Detection & Change Analysis · YOLOv11l-seg + 2DCNN**

배전설비 영상에서 전선·전주 등 주요 객체를 분할하고, 영상 간 구조적 변화와 이상을 탐지하는 연구입니다. KCI 등재 논문과 관련 실험 코드, 대표 결과를 함께 정리했습니다.

[논문 원문](https://www.kism.or.kr/file/memoir/14_8_7.pdf) · [DOI](https://doi.org/10.30693/SMJ.2025.14.8.60) · [KCI](https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART003234567) · [주요 코드](#주요-코드) · [인용](#인용)

## 논문 소개

### 딥러닝 기반 객체 탐지를 활용한 배전공가 이상 탐지 모델 연구

**이훈제**, 김진성, 정세훈, 심춘보<br>
스마트미디어저널 (*Smart Media Journal*), **14(8), 60–72**, 2025년 8월

논문은 **YOLOv11l-seg와 2DCNN을 결합한 이상 탐지 모델**을 다룹니다. 세그멘테이션 레이블링과 데이터 증강을 적용하고, 다섯 가지 객체 탐지 모델을 비교해 배전공가 영상 분석에 활용했습니다.

| 데이터셋 | 객체 레이블 | YOLOv11l-seg mAP@50 |
|:---:|:---:|:---:|
| **4,475장** | **56,797개 · 3개 클래스** | **0.830** |

데이터 규모는 논문 63쪽, 성능은 68쪽에 보고된 값입니다. 데이터는 학습 **3,585장** · 검증 **443장** · 시험 **447장**으로 구성되며, 클래스는 **Wire · Crossarm · Pole**입니다. [논문 원문](https://www.kism.or.kr/file/memoir/14_8_7.pdf)

## 대표 결과

![두 배전설비 영상을 비교하고 추가된 영역을 녹색 상자로 표시한 변화 탐지 사례](results/representative/change_detection_success.png)

*보관된 실험의 변화 탐지 사례. 오른쪽 영상의 추가된 영역을 `Added`로 표시했습니다.*

<details>
<summary>비교 방법별 시각화 더 보기</summary>

![영상 비교 방법별 변화 영역 시각화](results/representative/methods_comparison.jpg)

이미지에 표시된 변화율은 해당 영상 쌍의 출력값입니다. 전체 데이터셋의 정확도를 뜻하지 않습니다. 이미지별 원본 위치는 [대표 결과 안내](results/representative/README.md)에 기록했습니다.

</details>

## 모델 비교

논문 68쪽에 수록된 모델별 평가 결과입니다. **YOLOv11l-seg** 행은 제안 연구에 사용된 모델을 표시합니다.

| 모델 | F1 | Precision | Recall | mAP@50 | mAP@50:95 |
|:---|---:|---:|---:|---:|---:|
| Mask R-CNN | 0.573 | 0.542 | 0.581 | 0.566 | 0.237 |
| ConvNeXt | 0.596 | 0.599 | 0.626 | 0.568 | 0.249 |
| YOLOv8l-seg | 0.828 | 0.865 | 0.826 | 0.830 | 0.457 |
| YOLOv9c-seg | 0.817 | 0.842 | 0.828 | 0.807 | 0.417 |
| **YOLOv11l-seg** | **0.820** | **0.864** | **0.810** | **0.830** | **0.449** |

YOLOv11l-seg와 YOLOv8l-seg의 mAP@50은 **0.830**으로 같으며, F1과 mAP@50:95는 YOLOv8l-seg가 더 높습니다. 위 값은 객체 탐지 모델의 평가 지표로, 변화·이상 탐지 전체 과정의 정확도를 의미하지 않습니다. [출처: 논문 68쪽](https://www.kism.or.kr/file/memoir/14_8_7.pdf#page=9)

표의 수치는 [모델 비교 노트북](notebooks/analysis/chart.ipynb)에 기록된 값과 대조했습니다. 이번 공개 정리 과정에서 학습·평가를 다시 실행한 값은 아닙니다.

## 연구 구성

- **객체 탐지·분할:** 세그멘테이션 레이블과 데이터 증강을 활용한 모델 학습 및 비교
- **변화·이상 탐지:** YOLOv11l-seg와 2DCNN을 결합한 배전공가 영상 분석
- **결과 분석:** 영상 차이, 변화 영역 표시, 비교 그래프를 통한 결과 시각화

관련 기술: **Python · PyTorch · Ultralytics · OpenCV · Detectron2 · MMDetection**

## 주요 코드

| 살펴볼 내용 | 노트북 |
|:---|:---|
| 2DCNN과 YOLOv11을 이용한 영상 비교 | [2DCNN + YOLOv11](notebooks/research/2DCNN%2BYOLOv11.ipynb) |
| YOLOv11 세그멘테이션 학습·추론 실험 | [YOLOv11](notebooks/experiments/YOLOv11.ipynb) |
| 배전공가 변화·이상 탐지 실험 | [모델 이상 탐지](notebooks/research/모델%20이상%20탐지.ipynb) |
| 모델별 정량 결과와 비교 그래프 | [chart](notebooks/analysis/chart.ipynb) |

비교 모델과 코드의 대응 관계는 [논문과 연구 코드 안내](docs/PAPER.md)에서 확인할 수 있습니다.

<details>
<summary>저장소 구조</summary>

```text
notebooks/
  research/             변화·이상 탐지 연구
  experiments/          모델별 학습·추론 실험
  analysis/             비교 그래프·영상 전처리
  legacy/               초기·참고 실험
src/sift/               특징점 기반 영상 비교
results/representative/ 대표 시각화 결과
docs/                   논문·환경·데이터·파일 출처 안내
CITATION.cff            논문 인용 메타데이터
CITATION.bib            BibTeX
```

</details>

## 실행 및 자료 안내

이 저장소는 **연구 노트북 아카이브**입니다. 실행하려면 선택한 노트북의 데이터·가중치 경로를 수정하고 해당 모델의 환경을 준비해야 합니다. 노트북에는 원본 코드 셀을 보존했으며, 공개 사본의 저장된 출력과 실행 번호를 제거했습니다.

원본 데이터, 모델 가중치, 전체 학습 로그와 원본 노트북 출력은 로컬 아카이브에 별도로 보관합니다. 공개 저장소에는 코드·문서·대표 결과를 포함했습니다.

[환경 및 실행 안내](docs/ENVIRONMENT.md) · [데이터·모델 보관 안내](docs/DATA_AND_MODELS.md) · [원본 파일 대응표](docs/FILE_PROVENANCE.csv)

## 인용

> 이훈제, 김진성, 정세훈, 심춘보. (2025). 딥러닝 기반 객체 탐지를 활용한 배전공가 이상 탐지 모델 연구. *스마트미디어저널*, 14(8), 60–72. https://doi.org/10.30693/SMJ.2025.14.8.60

[BibTeX 다운로드](CITATION.bib) · [CITATION.cff](CITATION.cff)

논문 원문은 학회 공식 링크로 제공합니다. PDF 재배포와 코드 라이선스에 관한 확인 범위는 [논문 안내](docs/PAPER.md#pdf-공개-범위)를 참고해 주세요.

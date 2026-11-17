# Image Comparison Scripts

영상 비교 스크립트 5개입니다. 코드 내용은 이전 공개본과 동일하며, 용도에 맞게 폴더와 파일명만 정리했습니다.

| File | Method | Input images |
|---|---|---|
| [orb_matching.py](feature_matching/orb_matching.py) | ORB 특징점 비교 | Test.jpg, Test5.jpg |
| [sift_bf_matching.py](feature_matching/sift_bf_matching.py) | SIFT + BF matcher | Test.jpg, Test5.jpg |
| [sift_flann_matching.py](feature_matching/sift_flann_matching.py) | SIFT + FLANN | Test4.jpg, Test5.jpg |
| [sift_change_detection.py](feature_matching/sift_change_detection.py) | SIFT 기반 영상 차이 분석 | Test4.jpg, Test5.jpg |
| [yolov5_change_detection.py](baselines/yolov5_change_detection.py) | YOLOv5 검출 결과와 영상 차이 | Test4.jpg, Test5.jpg |

입력 파일은 **현재 작업 디렉터리** 기준입니다. 원본 이미지는 로컬 자료의 legacy/Sift 알고리즘에 보관되어 있으며, 공개본에는 포함하지 않습니다. 스크립트를 실행하기 전에 입력 경로와 해당 OpenCV/PyTorch 환경을 준비하세요.

The image names above are resolved relative to the **current working directory**, not the script location. Configure input paths before running. The YOLOv5 script uses detection rendering and image differences; its historical filename contained “sift”, but it does not call SIFT.

[Code map](../docs/CODE_MAP.md) · [Environment notes](../docs/ENVIRONMENT.md) · [Project overview](../README.md)

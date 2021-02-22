# MaskDetector
이 프로젝트는 훈련된 COVID-19 안면 마스크 감지기를 만들고, 다음 두가지 Python 스크립트를 구현할 수 있습니다.
- 이미지에서 COVID-19 안면 마스크 감지
- 실시간 비디오 스트림에서 안면 마스크 감지

# From 
|Title|Explanation|Other|
|:-----:|:-------:|:--------:|
|detect_mask_image.py|이미지에서 감지|For Covid-19|
|detect_mask_video.py|실시간 비디오 스트림에서 감지|https://github.com/kairess/mask-detection|
|train_mask_detector.py|마스크 디텍터 훈련|https://www.pyimagesearch.com/2020/05/04/covid-19-face-mask-detector-with-opencv-keras-tensorflow-and-deep-learning/ 참고|

# Explanation
- 커스텀 안면 마스크 감지기를 학습 시키기 위해서는, 우선 프로젝트를 두 단계를 나누고, 각 단계에는 각각의 하위 단계가 존재해야 합니다.
- 훈련 : 디스크에서 안면 마스크 감지 데이터 세트를 로드하고, 이 데이터 세트에서 모델(keras/Tensorflow)을 훈련 한 후에 마스크 감지기를 디스크에 직렬화 시켜줍니다.
- 배포 : 안면 마스크 감지기가 학습되면 마스크 감지기를 로드한 후, 얼굴 감지를 수행한 다음 각 얼굴을 다음과 같이 분류할 수 있습니다 (with_mask Or without_mask)

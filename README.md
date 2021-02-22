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
- 안면 마스크 감지 데이터 세트는 "마스크 포함" 및 "마스크 없음" 이미지로 구성됩니다, 데이터 세트를 사용하여 Python, OpenCV 및 Tensorflow / Keras를 사용하는 컴퓨터 비전 및 딥러닝이 포함된 COVID-19 안면 마스크 탐지기를 구축합니다.<br/>
<center><img src="https://user-images.githubusercontent.com/79067558/108645734-2582b800-74f7-11eb-85c7-056be26bfb21.png"></center>

# How to work
- 학습에 사용될 데이터는 많으면 많을수록 좋습니다 (업로드 용량제한 때문에, 일부 자료를 삭제하여 업로드 한 점 양해 부탁드립니다.)
- 기본적으로 높은 정확도를 위해서는 1400여개에 가까운 예시의 사진들이 필요하며 (착용/미착용 각각), 물론 이보다 더 많으면 많을수록 더욱 높은 정확도를 보여줍니다.
- Facial Landmark를 사용하여, 안면 마스크를 착용 한 얼굴 데이터 세트를 작성하기 위해서는 먼저 안면 마스크를 착용하지 않은 사람의 이미지로 시작해야 합니다.
- 그 다음 '얼굴 감지'를 적용하여 이미지에서 얼굴의 경계 상자 위치를 계산하게 됩니다.
- 이미지에서 얼굴이 어디에 있는지 알고 나면 얼굴 ROI(Region of Interest)를 추출할 수 있게 됩니다.
- 그 다음, OpenCV 및 Numpy 슬라이싱으로 얼굴 ROI를 추출합니다, 여기에서 'Face Landmark'를 적용하고 눈, 코, 입 등을 국소화 할 수 있게 됩니다.
- 후에 dlib를 사용하여 'Face Landmark'를 감지하고 얼굴에 마스크를 어디에 배치할 것인지를 알 수 있게 됩니다.

# Execution Sequence
- 첨부된 train_mask_detector.py를 먼저 구동시켜 줍니다.<br/>
  하고나면, 'Training Loss'와 'Accuracy' 결과값이 띄워지고<br/>
  동시에, 'mask_detector.model'이 저장이 될 것입니다.
  
- 그 다음부터는, mask_image.py와 video.py 순서대로 구동시키면 됩니다.
- 순서대로 구동하시다보면 어떤 방식으로 작동이 되며, 어떻게 결과값을 표시하게 되는지 아실 수 있을 것입니다.
- 물론 비디오 판독이라해서 반드시 mp4형식과 같은 영상뿐 아니라, 유튜브 url을 긁어옴으로 재생되는 영상에 대하여 감지하는 부분 또한 구현이 가능합니다.

# Author
Ian/@Ian0720 (aoa8538@gmail.com)

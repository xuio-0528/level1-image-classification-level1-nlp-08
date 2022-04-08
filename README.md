# level1-image-classification-level1-nlp-8

김은기, 김덕래, 허치영, 김용희, 이승환

<img width="1024" alt="image" src="https://user-images.githubusercontent.com/81913386/162423001-cc0546e7-efc0-46e2-8396-8db77454aeb8.png">


**Task : 마스크 이미지 분류\[나이(30대 미안, 30대 이상 60대 미만, 60대 이상) 마스크 여부(착용, 미착용 오착용), 성별(남, 여)]**

## Results
- Test dataset for public dataset
  - F1 score: 0.6779 / test accuracy: 72.5238
  - Provisional standing: 48th
- Test dataset for private dataset
  - F1 score: 0.6671 / test accuracy: 73.3333
  - Provisional standing: 48th

## 사용모델
- Age, Gender - Convnext
  - learning rate : 0.0005, loss : FCLS(gamma 2, labelsmoothing 0.1), Lr decay : 1 l optimizer : AdamW, Reszie : 224 x 224, Scheduler : Lambda(gender = StepLR) l dropout : 0.5, val batch 200
- Mask : Coatnet
  - learning rate : 0.001, Epoch 15, loss : crossentropy, Lr decay : 3 l optimizer : Adam, Reszie : 224 x 224, Scheduler : Lambda,
l dropout : 0.5, val batch 100

## Image Dataset Specifications
- 사진 속의 인물: 4500명
- 인물 당 사진: 7장
- 마스크를 제대로 착용한 사진: 5장
- 마스크를 잘못 착용한 사진: 1장 / 마스크를 착용하지 않은 사진: 1장
- Dataset ratio
  - Train & validation dataset: 60%
  - Test dataset for public leaderboard: 20% / test dataset for private leaderboard: 20

## Main Difficulties
- Data imbalance
  - 겉보기 성별이 남성인 사진과 나이대가 60세 이상인 사진의 비율이 유의미하게 낮았음
- Label noise
  - Train & validation dataset에 잘못 분류된 사진이 209/18900장(1.11%) 있었음
  - Subtask cross dependency
  - **Subtask 3개 간의 상호 dependency로 인해 class 18개의 독립분포 가정이 위배됨**

## 회고
| 사실



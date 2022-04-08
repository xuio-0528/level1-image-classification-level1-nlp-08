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
- Age, Gender : Convnext
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
> 기존에는 하나의 모델로만 해결하고자 하거나 Boosting 모델, Bagging 모델을 통해 문제를 해결하려고 했다면 이번 에는 예측해야하는 target 들에 따라 각각의 모델을 구현해주고 결과를 종합해주는 방식으로 진행했습니다. 처음 해보는 실험이었지만 결과적으로 성능이 60% 후반대까지는 끌어올릴 수 있었습니다.
>
다시 한 번 속도보다 방향성이 중요하다는 것을 깨달았습니다. 불안감에 휩싸여 일단 뛰기부터 시작했던 저 스 스로를 상당히 반성하게 되었습니다. 이후에 대회에서는 baseline을 토대로 코드를 차근차근 파악하고 처음부터 조금씩 쌓아나가는 형태로 진행해보고자 합니다. 저 스스로를 믿고 차분히 진행하고 싶습니다. 마지막으로 Fast AI 부분을 완성하지 못하고 에러를 해결하다 대회가 종료된 것이 너무 아쉬워서 다음 대회 전까지 에러를 해결하고 완전히 파악한 이후에 도입해보고 싶습니다.





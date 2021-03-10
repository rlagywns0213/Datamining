# Datamining ( 2020-2 )

## Prerequisites

- Python 3.6+
- Pandas
- Sklearn
- Tensorflow

## Process

### 1. Data


- [질병관리본부 국민건강영양조사](https://knhanes.cdc.go.kr/knhanes/sub03/sub03_02_02.do) 데이터

The `datasets` directory should look like:

    datasets
    ├── dataset
    │   ├── hn16_all.sas7bdat
    │   └── hn17_all.sas7bdat
    │   └── hn18_all.sas7bdat
    │       
    └── Derived data
        ├── delete_null.csv
        └── mean_null.csv
        └── mode_null.csv

### 2. Introduction

- 세계 비만 인구는 2008년 기준 총 14억 명, 매년 약 280만 명이 비만 관련 질병으로 사망
- 청소년기 비만은 성인으로 이어질 확률이 높으며 따라서 Random Forest, Logistic Regression 등 분류 기법을 이용한 청소년 비만 사전 예측 및 청소년 비만 유발 요인 파악이 중요

### 3. Method

- 국민건강영양조사 및 청소년 건강행태 조사에 참여한 청소년 대상으로 분석 수행
- 기존에 발표된 청소년 비만 관련 논문을 바탕으로 Feature Selection
- EDA (탐색적 분석) : 다중 공선성, 데이터 시각화를 통한 Feature의 Value 분포, 통계량 등 확인
- Intermediate Report 연구 결과를 바탕으로 각 데이터별로 모델의 최고 성능을 보여준 결측치 처리 방법, 스케일링 여부, K = 5/10인 K-fold 교차 검증 수행
- 4가지 분류기법(Random Forest, Logistic Regression, SVM, MLP)사용
- 추가적으로 오버샘플링, PCA, K-Means 기법을 이용하여 모델의 Performance 변화를 확인
=> 모델 별 그리드 서치 수행하며 청소년 통합/남자/여자 데이터 각각에 대해 모델 수립.

### 3-1. 변수 생성

- BMI 파생변수 생성 후, 0과 1 로 비만인지 아닌지 구별
- 독립변수는 모두 Domain Knowledge 에 의거

### 3-2. Data preprocessing

      python datapreprocessing.py

- 국민건강영양조사 데이터는 설문조사 식으로 형성 되어, **8, 9 (모름, 무응답)** 에 대해 NA 처리를 해주어야 함
- 결측치가 다수이므로, 결측치 제거, 결측치 대체(평균값 대체) 등의 performance 를 비교


### 3. Modeling

- Randomforest, SVM, DNN 등의 performance 비교

### 4. Evaluation

- 최대한 비만 청소년을 집중적으로 선별해내기 위해, Precision보다 Recall의 성능을 선호
- 따라서, F2-score , ROC 등의 성능을 비교

### 5.1 Predictive Results

![image](https://user-images.githubusercontent.com/28617444/110588881-fa67bc00-81b8-11eb-882b-cdb282b9d6a9.png)

- 전체적으로 Logistic Regression이 F2 Score 우수
- 여자 데이터 예측 결과 Recall만 전체적으로 가장 높고 그 외 척도는 변별력이 없는 수치<br>
▶ F2 Score가 모델 성능 비교에 적합한 척도

- 오버 샘플링 후 모델 성능 크게 향상
-  K-fold Cross Validation K값 증가 효과 미미



### 5.2 Descriptive Results
![image](https://user-images.githubusercontent.com/28617444/110588984-2125f280-81b9-11eb-88c4-3332fbb1ba20.png)

- 청소년 남자 비만과 여자 비만에 유의미한 인자에 차이가 있음을 확인

### 6. Discussion

- 객관적 지표의 제공
    - 잠재적인 비만 청소년을 위한 예방교육 및 상담과 조기중재에 필요한 기초자료
    - PatientsLikeMe 가입자 수 증가의 데이터가 축적 : 수익이 증가할 것으로 기대


- 사회적 낙인에 민감한 청소년의 비만 예방 중요성 재고
  - 청소년의 경우 정신적으로 성숙하지 않아 더 민감
  - 지속적인 비만예방과 관리가 이루어질 수 있도록 학교에서의 제도적 환경의 노력이 개인적인 수준에서 건강생활습관 실천으로 이어지는 토대 형성


- 향후 활용방안
  - 비만 예측에 활용
  - 통합/남/녀 데이터별 비만 예방 정책이나. 건강 설문조사 항목 등에 효과적
  - 본 연구에서 제안한 4가지 기법의 성능 지표 비교를 통해 최적의 솔루션을 제시 가능
  - 향후 피처를 더 보완함으로써 Recall을 높이는 개선 작업 기대

### 7. Limitation

- 컴퓨팅 리소스의 한계
  - 팀원 개인이 가진 컴퓨팅 리소스 부족으로 인한 모든 데이터 사용 불가, 다양한 커널 트릭 사용 불가


- 가중치 적용의 한계
  - 다른 기에 해당하는 데이터를 가져올 때는 가중치를 처리해야하는 어려움
  - 국민건강영양조사 자료와 청소년 건강 행태조사 자료를 함께 사용하는 경우 가중치 정보의 부재


## References

- [한빛미디어] 핸즈온 머신러닝

## Author

HyoJun Kim / [blog](http://rlagywns0213.github.io/)

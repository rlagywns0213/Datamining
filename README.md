 # Datamining ( 2020-2 )

데이터마이닝 전공수업 프로젝트 (청소년 비만 예측)

1. 사용 데이터

- 질병관리본부 국민건강영양조사 데이터

2. 변수 생성

- BMI 파생변수 생성 후, 0과 1 로 비만인지 아닌지 구별
- 독립변수는 모두 Domain Knowledge 에 의거

3. Data preprocessing

- 국민건강영양조사 데이터는 설문조사 식으로 형성 되어, **8, 9 (모름, 무응답)** 에 대해 NA 처리를 해주어야 함
- 결측치가 다수이므로, 결측치 제거, 결측치 대체(평균값 대체) 등의 performance 를 비교

4. Modeling

- Randomforest, SVM, DNN 등의 performance 비교

5. Evaluation

- 최대한 비만 청소년을 집중적으로 선별해내기 위해, Precision보다 Recall의 성능을 선호
- 따라서, F2-score , ROC 등의 성능을 비교

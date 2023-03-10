# 신용카드 대금 연체 예측
## AI_12_section2

### 문제정의

금융업계에서는 데이터, AI(인공지능) 등을 활용한 혁신적인 디지털 기술을 필요로 하고 있다. 따라서 알고리즘 개발을 통해 금융 분야의 기술을 발전시킬 수 있다.

### 문제 해결과정

1. 데이콘에서 신용카드 사용자들의 개인 신상정보 데이터 수집
2. target => 'credit'(0,1,2)을 이진분류로 변환, 음수값은 양수값으로 변환, 필요한 컬럼('Age', 'ID') 생성, 이상치 제거, 로그변환, 무의미한 변수 제거, 상관관계 높은 변수 둘 중 하나 제거 등의 전처리
3. 머신러닝 모델 구현 및 모델 해석

### 데이터셋

- '데이콘'에서 수집한 신용카드 사용자들의 개인 신상정보 데이터
- 주요 컬럼
  - index
  - gender: 성별
  - car: 차량 소유 여부
  - reality: 부동산 소유 여부
  - child_num: 자녀 수
  - income_total: 연간 소득
  - income_type: 소득 분류
  - edu_type: 교육 수준
  - family_type: 결혼 여부
  - house_type: 생활 방식
  - DAYS_BIRTH: 출생일
                데이터 수집 당시 (0)부터 역으로 셈, 즉, -1은 데이터 수집일 하루 전에 태어났음을 의미)

  - DAYS_EMPLOYED: 업무 시작일
                데이터 수집 당시 (0)부터 역으로 셈, 즉, -1은 데이터 수집일 하루 전부터 일을 시작함을 의미, 양수 값은 고용되지 않은 상태를 의미함
  - FLAG_MOBIL: 핸드폰 소유 여부
  - work_phone: 업무용 전화 소유 여부
  - phone: 전화 소유 여부
  - email: 이메일 소유 여부
  - occyp_type: 직업 유형													
  - family_size: 가족 규모
  - begin_month: 신용카드 발급 월
                데이터 수집 당시 (0)부터 역으로 셈, 즉, -1은 데이터 수집일 한 달 전에 신용카드를 발급함을 의미

  - credit: 사용자의 신용카드 대금 연체를 기준으로 한 신용도
                 낮을 수록 높은 신용의 신용카드 사용자를 의미함
  
### 프로젝트 진행과정

1. 프로젝트 기획 및 데이터 수집
2. 데이터 전처리 및 시각화
3. 분석 모델 관련 학습 및 구현
4. 모델 해석 관련 학습 및 해석

### 결과정리

- Randomforest 모델과 XGBoost 모델 사용
- 평가지표는 auc_score로 두 모델 모두 0.71의 성능을 보임
- shap 라이브러리를 사용하여 모델 해석
- 특정 샘플을 뽑아 긍정적인 영향을 주는 특성(빨간색)과 부정적인 영향을 주는 특성(파란색) 확인

<img width="1057" alt="스크린샷 2023-02-21 오후 12 30 00" src="https://user-images.githubusercontent.com/49776542/220240370-f94f0f76-4c1d-49a1-9041-81d21b70acbf.png">

- 결론적으로 신용카드 대금 연체 예측을 할때 '신용카드 발급 월', '고객ID', '나이', '연간소득' 4가지의 특징이 중요하게 적용 된다는 사실을 확인

<img width="579" alt="스크린샷 2023-02-21 오후 12 28 18" src="https://user-images.githubusercontent.com/49776542/220240142-3b0c9607-b173-4bfb-a7e4-b15daed30fed.png">


### 한계점 및 해결방안

- 모델링 과정에서 하이퍼파라미터 조정하는 부분이 아쉬웠고 향후 성능을 높일 수 있는 방법에 대해 모색해 보면 좋을 것 같다.
- 불균형 클래스 문제에 대한 해결 방안을 사용해 보지 못해 베이스라인 모델의 성능이 더 좋게 나온 부분이 아쉬웠고 향후 발전시킬 예정이다.
- 분석을 위한 가설과 목적을 더 고민해 보고 명확한 결론을 내면 좋을 것 같다. 
- 모델 해석(shap) 부분을 더 공부해 볼 예정이다.

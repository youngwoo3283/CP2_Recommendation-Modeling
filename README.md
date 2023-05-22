### 추천모델링 파일 설명

AI_15_최영우,윤현욱_CS2_추천프로젝트 : 직접 제출한 다른 사람이 볼 수 있도록 정리한 코드

fashion_campus(1) : 최영우 직접 전처리하거나 여러 함수 및 eda등을 진행한 코드

click_data : 윤현욱 직접 전처리하거나 여러 함수 및 eda등을 진행한 코드

click_data_final : 현욱님이 직접 다른사람이 볼 수 있도록 정리한 코드


- 정리한 코드에는 데이터 프레임이 어떻게 생성되었나 이런거는 삭제하였고 해당코드들은 직접 전처리한 파일들에 있습니다!!



# CP2_Recommendation-Modeling

캐글에 있는 인도네시아 쇼핑몰 데이터인 fashion campus라는 데이터를 활용해서 추천 시스템을 구현하는 프로젝트 추천시스템은 svd, implicit, surprise등의 라이브러리를 사용하였고, martrix factorization와 통계적 시스템으로 추천을 구현함.

![image](https://github.com/youngwoo3283/CP2_Recommendation-Modeling/assets/69841073/c928e7a4-1f51-434d-8cb1-59a63f0e5818)



# 데이터셋 설명

customer : 고객의 정보 데이터
transaction_new : 고객의 거래 정보 데이터
click_data_new : 고객의 사이트에 대한 행동 데이터
product : 상품 정보 데이터

![image](https://github.com/youngwoo3283/CP2_Recommendation-Modeling/assets/69841073/159205f1-94ed-4e88-97af-4719d3142746)


# 진행 과정 

데이터를 전처리를 한후에 고객 세분화를 통해서 고객을 4분위로 나눈다음에 분위 고객에 따라서 다른 추천 시스템 파이프라인을 구축함. 먼저  원하는 상품을 입력하면 해당 고객의 정보에 따라서 몇분위 고객인지 확인한후에 1,2 분위 고객에게는 mf를 이용해서 해당 상품을 추천해줌. 반면 3,4분위의 고객에게는 고객 데이터가 부족해서 자연어처리를 통한 해당 상품과 비슷한 이름을 가진 상품들을 추천함. 만약 해당 고객에 대한 거래정보가 없거나 신규 고객의 경우는 판매량이 높은 순이나 최근 구매일 낮은 가격등의 통계적 시스템을 이용해서 추천해주도록 함. 

### 파이프 라인
![image](https://github.com/youngwoo3283/CP2_Recommendation-Modeling/assets/69841073/f0e2e779-cf25-4bf0-91fb-ee7e6ea6bb1f)

### 통계적 추천
![image](https://github.com/youngwoo3283/CP2_Recommendation-Modeling/assets/69841073/f3a0a344-2442-4e4e-a65b-1fbece4ce429)

### nlp를 이용한 추천
![image](https://github.com/youngwoo3283/CP2_Recommendation-Modeling/assets/69841073/5e0ca0db-b739-41df-a349-26fb723ae631)

### cf를 이용한 추천
![image](https://github.com/youngwoo3283/CP2_Recommendation-Modeling/assets/69841073/8109e5fc-4360-4b69-b438-10c18d6cb5b9)


# 진행 결과
먼저 프로그램을 실행하면 (함수 실행) 먼저 customerid를 입력함. 입력하면 다음에는 원하는 상품을 입력하도록 함. Shirts를 검색하면 먼저 기존 고객이면 세분화를 하고 맞는 추천시스템으로 추천하고 비회원이나 거래내역이 없으면 통계적 시스템으로 추천을 함. 이때 통계적 시스템은 판매량, 최근출시, 높은가격, 낮은 가격, 할인율 등의 옵션이 있고 원하는 옵션을 입력하면 해당 옵션으로 추천해줌. 1,2분위는 mf로 알맞는 shirts를 추천하고, 3,4분위는 shirts와 비슷한 이름을 가진 상품을 추천해줌




# 자체 평가
- 데이터가 양이 꽤 많아서 전처리 및 처리시에 어려웠다. Bigquery와 paquet 및 sql의 구체적인 학습 필요
- 거래내역이 없어서 비회원과 같은 경우에는 cb모델을 사용함
- 클릭데이터를 보니 모바일의 경우가 증가하는데 이에 대한 추천시스템 구분 필요
- Implicit한 데이터이다 보니 정확한 평가의 어려움, user_product_matrix의 재학습 및 추가적인 모델 학습 필요 
- NLP를 이용시 결측값이 있는 사용자에게는 추천을 못하는 오류 발생
- 고객세분화의 기준을 RFM으로 하였는데 이때 R,F,M사이에 가중치 부여 필요


# 느낀점

- 현재 넷플릭스나 유튜브에 쓰이는 추천시스템이 얼마나 정교하고 정확한 시스템인지를 깨닫게 됨

- 이런 소규모의 데이터도 어떤 과정을 하기 힘들다는 것을 깨달음

- 혼자하는 것보다 팀으로 프로젝트를 하니 더 수월하였고, 모르는 부분이나 몰랐던 부분을 소통을 통해서 해결함

- 시연해보면 시간은 엄청 오래 걸리지는 않지만 현재 상업적인 프로그램은 모두 시간이 짧아서 대단하다고 느낌 

- 자연스레 추천시스템과 관련한 다양한 모델들을 공부할 수 있어서 만족스럽다.





프로젝트 목적: 데이터 공모전 플랫폼 데이콘에서 이커머스 고객 데이터를 활용해 유저 세분화를 진행하고 비즈니스 인사이트를 도출한다.

사용언어: python

유저세분화 기준: 

1.RFM 분석

1-1. Recency: 오늘날짜 - 고객ID별 가장 최근 거래날짜

Sales 데이터 중에서 고객ID column 과 거래날짜 column 을 이용해 Recency를 도출한다. 전체 거래날짜 중 가장 최근 날짜인 2019년 12월 31일을 오늘 날짜로 설정한 후, 거기에서 고객ID별 가장 최근 거래날짜를 뺀다.

1-2. Frequency: 고객ID별 거래ID row 수

고객 ID별 거래ID row 개수를 세어서, 고객 별로 몇 번의 구매를 진행하였는지 도출한다.

1-3. Monetary: 고객ID별 수량*평균금액의 합(ARPPU)

수량과 평균금액을 곱한 값인 총구매금액 column을 새로 만든다. 고객ID별로 총구매금액의 합을 도출해 Monetary 변수로 사용한다.

2.RFM을 토대로 고객세분화 진행

상기에 구한 Recency, Frequency, Monetary값들을 토대로 3분위 수를 구해 각각 Recent, Moderate, Past 혹은 High, Moderate, Low 값을 부여한다.

2-1. VIP고객

Recent, High, High 로 값이 도출될 경우 VIP고객으로 분류한다.

2-2. 잠재VIP(Promising) 고객

Recent, High 혹은 Moderate, High 혹은 Moderate 로 값이 도출될 경우 잠재VIP고객으로 분류한다.

2-3. 이탈VIP고객

Past, High, High 로 값이 도출될 경우 이탈VIP고객으로 분류한다.

2-4. 이탈고객

Past, Low, Low로 값이 도출될 경우 이탈고객으로 분류한다.

분석 내용:

1. 고객 군별 인구 통계학적 정보: 지역, 성별

2. 제품 군별 분석

3. 고객 군별 쿠폰 사용 여부

분석 결과:

![image](https://github.com/RileyJYR/E-commerce-segmentation/assets/168352023/52ce3987-f802-4294-bf4b-a1d0a802485d)
![image](https://github.com/RileyJYR/E-commerce-segmentation/assets/168352023/b1890510-0507-4e17-b293-50b3cb323d73)
![image](https://github.com/RileyJYR/E-commerce-segmentation/assets/168352023/c8620548-d1e7-4881-825c-b3632cd5eae0)
![image](https://github.com/RileyJYR/E-commerce-segmentation/assets/168352023/37d6bbfd-a71c-41df-8934-f1219ddac781)

도출 인사이트:

1-1. 지역: 대부분의 고객 군이 공통적으로 California, Chicago, New York 순으로 많았으나, 이탈 VIP고객만 Chicago에 가장 많은 특징을 보였다. 해당 지역에서 코어 고객을 놓치게 된 이벤트는 없었는지 주력할 필요가 있다. 여타 지역과 다른 점이 있었는지, 있었다면 무엇인지, 이를 해결할 방안은 무엇인지 논의가 필요하다.

1-2. 성별: 모든 고객 군 통틀어서 여성고객이 남성고객보다 2배가량 더 많은 양상을 띈다. 그러나 이탈고객은 타 고객 군에 비해 여성고객의 비중이 더 높다. 해당 제품 군에서 여성 소비자의 이탈을 유도한 요인은 무엇인지 분석하고, 이를 해결하기 위한 논의가 필요하다.
높은 여성 소비자의 비중을 고려하여, VIP 여성고객을 Lock-in 할 방안, 잠재 VIP 여성고객을 VIP고객으로 만들 방안을 고민해야 한다.

1-3. 제품군: Nest 제품의 VIP, 잠재VIP, 이탈VIP, 이탈고객의 수를 조회해 본 결과, 타 제품군에 비해 이탈고객의 수가 많은 양상을 띄고 있었다. 기업 이윤에 도움이 되어야 할 제품의 고객들이 이탈을 했다는 뜻으로, 해당 제품군 마케팅을 검토하여야 한다.

1-4. 쿠폰: 고객군별 쿠폰 사용여부에 큰 차이는 없는 걸로 봐서, 할인쿠폰이 유효한 마케팅 전략이라고 보기 힘들다. 특정 고객 군을 타켓팅한 쿠폰을 발급하여 그들의 구매를 유도하는 것이 바람직할 것이다. 잠재 VIP 고객을 타켓팅하여 높은 할인율의 쿠폰을 발급한다면, 이미 이탈한 고객에게 비용을 사용하지 않으면서도 효과적인 구매촉진을 이룰 수 있다.

## Installation
 Install plotly
 ```
 !pip install dash
 ```
 If jupyter notebook 
 ```
 pip install jupyter-dash
 ```
 
 # Video Game Analysis
 
 ### 데이터 전처리 
 > Year, Genre (이상치 및 결측치) 수정 
 >> 1. Year(결측치) - 2005년으로 수정
 >> 2. Year(이상치) - 20보다 작은 경우 2000을 더함 , 20보다 큰 경우 1900을 더함
 >> 3. Genre(결측치) - KMeans 클러스터링으로 Genre 추측
 >> 4. Year 별 트렌드 파악하기 위해 1990, 2000, 2010으로 [new_year] feature 생성
 >> 5. 총 판매량을 [Total_Sales] feature 생성
 
 ### 연도별 트랜드
 > ```pd.crosstab(Index = [Year], columns = [Genre], values = [Total_Sales]) 사용```
 >> np.where을 이용해 큰 값만 추출 후 plotly.bar 시각화 
 
 ### 나라별 선호도
 > ```pd.crosstab(index=[Platform], columns=[Genre], values=[NA, EU, JP, OS]) 함수로 만들어 생성```
 >> plotly.scatter 시각화
 
 ### 종류별 출고량 
 > * 게임 총 판매량을 plotly.pi 사용
 > * 연도별 (1990, 2000, 2010) 3개 그룹을 만들어 plotly.pi 표현
 > * 2010년 이후 매출이 높은 그룹, 2000년 이후 매출이 높은 그룹 확인
 
 
 ### 3개 그룹에 대한 분석 및 시각화
 >> 정밀한 트랜드 파악 목적
 >> * 개수확인
 >> * 3개 그룹 중 현재와 가까운 2그룹 게임 발매 수 시각화 
 >> * 현재와 가까운 2개 그룹에 나라별 데이터 정리 
 >> * 현재와 가까운 2개 그룹에 높은 판매율을 가진 게임 종목(Action, Shooter, Role-Playing)에 대한 플랫폼별 판매량
 >> * 현재와 가까운 2개 그룹에 대한 플랫폼별 판매량
 >> * 현재와 가까운 2개 그룹에 나라별 선호도 
 
 ## 분석 결과
* 발매 수에 따라 판매량이 어느 정도 연관성을 띄고 나라별 선호도가 비슷하며
* 엑스박스와 플레이스테이션, Wii 플랫폼이 큰 인기를 얻고있다.
#### 추천하는 게임 종목
>> 1. Shooter 게임은 게임 발매수가 1.8배 차이(2000 VS 2010년도)가 나지만 판매율은 높게 나타난다.
>> 2. Role-playing 발매 수가 차이가 많이나지 않고 연도별 꾸준한 인기를 얻고있다라고 보여진다. 
>> 3. Action 게임 발매수 가장 높고 발매수 차이가 많이나지않고 꾸준한 판매율이 나타난다.

 

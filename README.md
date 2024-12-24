## 🏥전국 의료시설 현황 분석 및 동적 시각화 앱 개발
<br>

## 1. 프로젝트 배경 및 목적
전국적으로 **지역 간 의료 자원의 분포가 불균등**하며, 이로 인한 지역사회의 의료 접근성 차이가 크다.<br>
특히, 코로나19 팬데믹 기간 동안 **의료 공백 문제**가 대두되었다.<br>
일부 지역에서는 충분한 의료 시설과 인력이 확보되지 않아, 시민들이 필요한 의료 서비스를 제때 받지 못하는 경우가 발생했다.<br>

본 프로젝트는 **전국의 의료시설 현황을 체계적으로 분석**하여, **의료 자원 불균형 문제를 개선하기 위한 방안을 모색**한다.<br>
또한 Streamlit을 활용하여 **동적 시각화 앱을 개발**함으로써 사용자가 직접 다양한 데이터를 조합하고 분석할 수 있도록 지원한다.
<br>
<br>

## 2. 주관 & 프로젝트 기간
- [전공 수업] 빅데이터처리와시각화
- 2022.05 - 2022.06
<br>

## 3. 분석 과정
### 3.1. 데이터 수집
- **건강보험심사평가원 - 전국 병의원 및 약국 현황 데이터**<br>
  건강보함심사평가원에서 제공하는 데이터를 활용하여 전국의 병의원, 약국 등 의료시설의 현황을 분석하였다.<br>
  해당 데이터에는 의료기관의 위치, 종류, 운영 현황 등이 포함되어 있다.

- **전국 인구데이터**<br>
  통계청에서 제공하는 인구 데이터를 활용하여 각 지역별 인구 수와 연령별, 성별, 인구 분포를 분석하였다.<br>
  이를 통해 지역별 의료 수요를 추정하고, 의료시설 분포와 비교하는 데 사용하였다.<br>
<br>

### 3.2. 데이터 전처리
- **중복값 제거**<br>
  수집된 데이터셋에서 중복된 데이터를 제거하여 데이터의 품질을 개선하였다.<br>
  특히, 의료시설 데이터에서 동일한 기관이 중복 등록된 경우를 식별하고 제거하였다.<br>

- **결측치 처리**<br>
  의료기관 데이터에서 '요양기관명', '종별코드명', '시도코드명'과 같은 필수 정보가 누락된 데이터는 전체 데이터셋에서 제거하였다.<br>
  인구 데이터에서 일부 연령별 인구수에 대한 결측치는 해당 지역의 다른 연령대 정보를 사용하여 비례적으로 계산하거나, 인근 지역의 유사한 패턴을 참고하여 대체하였다.<br>
  의료기관의 위치 정보(위도 및 경도)가 누락된 경우, 해당 의료기관의 주소 정보를 활용하여 지리적 위치 데이터를 다시 수집하거나 동일 지역 내 다른 기관의 평균 좌표를 사용하여 대체하였다.<br>

- **데이터 라벨링**<br>
  각 의료기관에 대한 데이터에 지역 코드, 시설 종류 등을 포함하여 라벨을 추가함으로써 데이터의 가독성을 높이고, 분석 과정에서의 필터링과 그룹화 작업을 용이하게 하였다.<br>
  또한, 각 지역별 인구 데이터에 연령대별 인구 수를 포함시켜 더욱 세부적인 분석을 가능하게 하였다.<br>
- **데이터 병합**<br>
  지역별 의료기관 데이터와 인구 통계를 병합하여 하나의 통합 데이터 프레임을 생성하였다.<br>
  이를 통해 의료 자원과 인구 수요 간의 상관 관계를 효과적으로 분석할 수 있었다.<br>
<br>

### 3.3. 데이터 분석
- **전국 의원 및 병원**<br>
  전국의 의원 및 병원 분포를 시각화하여 분석한 결과, 의료 시설이 수도권에 집중되어 있는 현상이 확인되었다.<br>
  특히 서울, 경기 지역에는 다른 지역에 비해 월등히 많은 의료기관이 위치하고 있어, 지역 간 의료 접근성에 큰 차이가 있음을 시사한다.
  <br>
  <br>
  <img src="https://github.com/user-attachments/assets/86cb3904-6e7d-4960-aae6-088492bfac61" width="300" height="182"/>
  <img src="https://github.com/user-attachments/assets/07aa90a8-557d-4264-af7b-76eefef9f0f6" width="246" height="195"/>
  
  
- **인구 수 대비 의료시설 비율**<br>
  각 지역의 인구 수를 고려하여 의료시설 비율을 분석한 결과, 서울은 인구 수 대비 의료시설이 타 지역에 비해 약 2배 이상 많은 것으로 나타났다.<br>
  이는 서울이 의료 자원의 집중도가 가장 높은 지역임을 보여준다.
  <br>
  <br>
  <img src="https://github.com/user-attachments/assets/829f1542-3389-4354-b990-62f2ff7f4039" width="280" height="250"/>
  

- **응급실 운영 병원 비율**<br>
  전국적으로 응급실을 운영하는 병원의 비율은 약 3%에 불과하며, 이 중 대다수가 수도권에 집중되어 있다.<br>
  응급의료 서비스의 접근성이 낮은 지역이 많아, 신속한 응급의료 대응에 문제가 있을 수 있음을 시사한다.
  <br>
  <br>
  <img src="https://github.com/user-attachments/assets/6ae67539-b878-4db7-b1fb-ce3858ab27c8" width="280" height="250"/>
  

- **전문병원 분포**<br>
  전국에 있는 전문병원은 약 100여 개에 불과하며, 이 중 절반이 서울과 경기 지역에 위치하고 있다.<br>
  반면, 강원, 충남, 제주 등 일부 지역에는 전문병원이 전혀 없어, 고도의 전문 의료 서비스 접근에 심각한 지역적 불균형이 존재한다.
  <br>
  <br>
  <img src="https://github.com/user-attachments/assets/811173ce-6195-4e8e-8d72-32b2c5740975" width="280" height="250"/>
<br>

## 4. 동적 시각화 앱
Streamlit 라이브러리를 활용하여 전국 의료시설 현황을 확인할 수 있는 동적 시각화 앱을 개발하였다.<br>
이 앱은 사용자가 직접 다양한 데이터를 탐색하고 분석할 수 있는 도구로서, 다음과 같은 기능들을 제공한다.

- **인구 대비 의료시설 비율 분석**<br>
  각 지역의 인구 대비 의료시설 수를 계산하여 시각화한다.<br>
  사용자는 이 정보를 통해 어떤 지역이 상대적으로 의료 자원이 부족한지 파악할 수 있다.
    

- **진료과목별 의료시설 탐색**<br>
  사용자는 특정 진료과목을 선택하여 전국의 해당 진료과목을 운영하는 의료시설을 검색할 수 있다.<br>
  이는 특정 전문 의료 서비스의 접근성을 조사하는 데 유용하다.
    

- **응급실 운영 병원 탐색**<br>
  응급실을 운영하는 병원만을 필터링하여 표시하는 기능을 통해, 응급 의료 서비스에 대한 접근성을 지역별로 비교 분석할 수 있다.
    

- **전문병원 위치 정보 제공**<br>
  전문병원의 위치와 해당 병원이 전문화된 분야를 사용자가 쉽게 확인할 수 있도록 정보를 제공한다.
<br>

## 5. 결론
본 분석을 통해 확인된 의료시설의 수도권 집중 현상은 지방과 도시 간 의료 불균형을 심화시키고 있다.<br>
이에 지방에도 의료시설이 충분히 설립될 수 있도록 정책적 유인을 제공하여, **지방과 도시의 균형 있는 발전을 촉진**해야 한다.<br>
또한 의료 서비스의 효율성을 제고하고 **지역별 의료 자원을 최적화**하여, **응급 의료 서비스와 전문 병원 간의 지역 격차를 줄이는 전략**이 필요하다.
  

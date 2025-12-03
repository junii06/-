# ✈️Flight Demand & Load-factor Analysis(2022-2025)

## 🏠프로젝트 제목
항공 노선 수요·탑승률 분석 프로젝트

## 📌프로젝트 개요
코로나 이후 관광수요가 회복됨에 따라 급변하는 항공산업의 흐름을 파악하고자 하였다.
</bn>
본 프로젝트는 2022.07~2025.06의 공공 항공 데이터를 활용하여:
</bn>
본 프로젝트를 통해:
- 년도·월별 수요 추이
- 동/하절기 인기노선·여행지
- 항공사 시장 점유율
- 환승 패턴
- 탑승률 영향 요인
까지 종합 분석하는 프로젝트이다.

## 🔍분석 프로세스
1) air_route_preprocessing.ipynb
  - raw 데이터 로딩
  - 컬럼명 통일 및 데이터 병합, 불필요 데이터 삭제
  - 결측치 확인
  - 데이터 형태 변환(str->datetime, str->int64)
  - 파생변수 생성(총여객(명), 항공화물(kg), 평균탑승객(명/편)_proxy)
  - 공항코드 데이터 매핑
  - 여객용, 화물용 데이터 분리, 개별 저장
</bn>
2) air_route_analysis.ipynb
  - 여객용 데이터 로딩, 데이터 확인
  - 년도·월별 총여객 추세 시각화
  - peak 동·하절기 노선 탐색
  - 인기 여행지 top10 분석(peak, 상대적 nonpeak 기반)
  - 항공사 시장 점유율 비교
  - 환승 공항/항공사 top10 분석
  - LGBM 기반 탑승률 예측 모델 구축
  - SHAP 기반 영향 요인 분석

## 💡주요 분석 결과



## 🧰사용 기술 및 라이브러리
언어
- Python
</bn>
라이브러리
- glob: 파일명 조회
- pandas: 데이터 불러오기, 데이터 병합, 데이터 형태 변환, 데이터프레임 형태로 저장, 인코딩(one-hot)
- datetime: 문자열 데이터 → datetime 형태로 변환
- matplotlib : 시각화
- plotly.express : 계층형 트리 구조 시각화
- sklearn : 전처리(LabelEncoder), 모델링(RandomForest, Linear), 평가(RMSE, MSE, MAE, r2)
- LightGBM : 모델링
- shap : 탑승률 주요 영향 요인 분석

## 📂폴더 구조
AIR_ROUTE_ANALYSIS/
├── data/ # RAW 데이터, 전처리 완료 데이터, test데이터 모델링
│ ├── 노선별 항공사별 항공운송실적(2022년 전체).csv
│ ├── 노선별 항공사별 항공운송실적(2023년 전체).csv
│ ├── 노선별 항공사별 항공운송실적(2024년 전체).csv
│ ├── 노선별 항공사별 항공운송실적(2025년 01~07).csv
│ ├── 국토교통부_세계공항_정보_20241231.csv
│ ├── passenger_analysis.csv
│ ├── pred_result.csv
│
├── notebooks/ # 전처리, 분석 코드
│ ├── 01_air_route_preprocessing.ipynb
│ ├── 02_air_route_analysis.ipynb
│
├── results/ # 분석 결과 시각화 이미지
│ ├── 01_년도·월별 총여객 추이.png
│ ├── 02_월별 총여객 증감률(%).png
│ ├── 03_peak 하절기,동절기 인기 여행지 top10.png
│ ├── 04_상대적 nonpeak 인기 여행지 top10.png
│ ├── 05_년도별 국제·국내선 항공사 점유율(%).png
│ ├── 06_공항별 아시아태평양 환승수요 top10.png
│ ├── 07_항공사별 환승수요 top10.png
│ ├── 08_항공사별 환승수요 top10(국적기 제외).png
│ └── 09_탑승률 영향 요인(영향구조).png
│ └── 10_탑승률 영향 요인(중요도).png
│
└── README.md



## ⚠한계점
- 실제 좌석 공급량 데이터 부재 → 탑승률 추정에 한계








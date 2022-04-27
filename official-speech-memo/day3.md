[Youtube](https://www.youtube.com/watch?v=sBH7Ly8sh-Y)

---

### Hospitality 산업이란,

숙박, 음식 및 음료 서비스, 이벤트

체크인 체크아웃 등 고객과 소통하며 효율적으로 구성해야 함

타 사이트와의 연계 등 필수적으로 IoT가 중요함

## 사용 서비스들

### **AWS IoT Greengrass**

앞단에서 사용자 행동에 따라 서비스를 제공

- 머신러닝 기반 추론
- 자료 전처리
- 장비 관리

### AWS Glue

수집된 자료를 저장하고 처리하는 서비스

- Glue Crawlers
- Glue Connectors
- Glue Data Catalog

### EMR, Redshift

→ 대량의 데이터를 거의 실시간으로 분석할 수 있게 됨. 

### Amazon Athena

분석 플랫폼 구축 시 도입을 빠르게 진행해주는 서비스

---

# 야놀자 서비스에 적용하기

### 데이터 흐름 이중화

실시간 이벤트에 대한 요구사항과 함께 대사 처리, 일별 Cold Data 재생산을 위하여, 배치 파이프라인을 추가 활용하였다. 

<img width="671" alt="image" src="https://user-images.githubusercontent.com/61778930/165470547-a8085a46-eb1a-46bc-ac89-0ff1e7d83c6a.png">


### 데이터 플로우

<img width="858" alt="image" src="https://user-images.githubusercontent.com/61778930/165470647-00f94f88-53a2-4e82-9668-e9adb3564f83.png">

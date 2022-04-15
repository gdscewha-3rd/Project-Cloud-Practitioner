# Amazon EKS 소개 및 AWS의 Observability 옵션 [AWS Builders Standard Edition]
[Youtube](https://www.youtube.com/watch?v=349ywnrrROg&t=158s)

# Observability 의 요인들

- Metrics
- Logs
- Traces

# 1. Metrics

- Amazon CloudWatch Container Insights
    - 
- Amazon Managed Service for Prometheus
    - 프로메테우스를 사용하는 경우, 매니징하는 데 편리해짐

# 2. Logs

어디에 저장할 것인가?

- Amazon CloudWatch
- Amazon ElasticSearch
    - 실시간 분석에 유리함.
- Amazon S3 + Kinesis + Athena
    - S3에 데이터를 넣고 Athena 와 연결하여 SQL문 수행 &분석
    - 가장 저렴한 솔루션

# 3. Traces

→ **AWS X-Ray**

어디서 시간을 많이 잡아먹는지 등 분석

전체 분산 시스템에 대한 변곡 지점 확인 → trace 분석하여 고쳐나갈 수 있게 문제 분석해주는 것

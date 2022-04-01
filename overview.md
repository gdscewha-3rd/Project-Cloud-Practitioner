# 1단계: AWS 백서 정리하기


# 주요 서비스 Overview
<img width="835" alt="overview-1" src="https://user-images.githubusercontent.com/61778930/161017929-7b9a98f4-20d8-4f67-a93d-a3ab9645200b.png">

### 컴퓨팅

- **EC2** : Elastic Computing Cloud로, 탄력적인 클라우드 서버   
- **EC2 Container Service** : 도커 컨테이너를 지원하는 컨테이너 관리 서비스   
- **EC2 Container Registry** : 완전관리형 도커 컨테이너 레지스트리 (개발자가 도커 컨테이너 이미지를 손쉽게 저장, 관리, 배포할 수 있게 해줌)   
- **Amazon Lightsail** : 가상 프라이빗 서버를 시작하고 관리할 때 사용할 수 있는 가장 간편한 방법   
- **AWS Batch** : 엔지니어가 AWS에서 수많은 배치 컴퓨팅 작업을 효율적으로 할 수 있게 해주는 서비스   
- **Amazon VPC** : AWS 계정 전용 가상 네트워크   
- **AWS Elastic Beanstalk** : 친숙한 서버(Java, NodeJS, ...)에서 개발된 웹 애플리케이션 및 서비스를 배포하고 확장하는 서비스   
- **AWS Lambda** : 서버리스 컴퓨팅 (서버 없이 코드만으로 업무 처리)   
- **Elastic Load Balancing** (Auto Scaling) : 애플리케이션 가용성을 유지하는 데 도움이 되고, 정의한 조건에 따라 EC2 용량을 자동으로 확장/축소 할 수 있다.   

### 네트워크

- **Amazon VPC** : AWS 계정 전용 가상 네트워크
- **Amazon CloudFront** : CDN. 전세계의 Edge에서 컨텐츠를 미리 캐싱해두어 성능 가속.
- **Amazon Route 53** : 도메인 등록, 관리하는 DNS 서비스. (서버 다운 시 다른 곳으로 routing 해줌)
- **AWS Direct Connect** : On-prem에서 AWS로 전용 네트워크 **연결**을 쉽게 설정
- **Elastic Load Balancing** : 트래픽 몰리면 EC2 인스턴스에 분산해서 배포해줌

### 스토리지

- **Amazon S3** : 객체 기반 스토리지. 심플하게 자주 저장하는 용도, 정적 웹사이트 호스팅 용도
- **Amazon EBS** : 블록 기반 스토리지. 영구적인 스토리지 용도.
- **Amazon EFS** : 네트워크 파일 시스템. 간단하고 확장 가능한 공유 파일 스토리지 솔루션
- **Amazon Glacier** : 아카이빙 용도. 장기 백업에 유리. Load 시에만 비용 발생
- **AWS Storage Gateway** : On-premise 데이터 스토리지를 AWS 클라우드에 연결하는 용도
- **AWS Snowball** : 페타바이트 규모의 대용량 데이터를 안전하게 전송하기 위함 (보통 on-prem → AWS 이동 용도)
    
    ### 데이터베이스
    
    - **AWS Aurora** : MySQL 및 PostgreSQL과 호환되는 관계형 데이터베이스 엔진, 필요에 따라 스토리지를 자동으로 늘리는. 비용 효율성 & 뛰어난 성능이 특징.
    - **AWS RDS** : 완전관리형 관계형 DB 서비스
    - **AWS DynamoDB** : NoSQL DB 서비스
    - **AWS ElastiCache** :  NoSQL DB 및 애플리케이션의 부하를 줄이는 데 탁월한 선택, 클라우드에서 인메모리 캐시를 손쉽게 배포, 운영, 조정할 수 있게 해주는 웹 서비스

### 보안 및 자격 증명

- **AWS IAM** : AWS 서비스및 리소스에 대한 액세스를 안전하게 관리. 사용자를 Allow/Deny
- **Amazon Inspector** : 자동화된 보안 평가 서비스. AWS에 배포된 애플리케이션의 보안 및 규정 준수를 평가함.
- **AWS Artifact**
- **AWS Certificate Manager**
- **AWS CloudHSM** : 클라우드 기반, AWS 클라우드에서 자체 암호화 키를 쉽게 생성하고 사용하게 해주는 하드웨어 보안 모듈(HSM).
- **AWS Directory Service**
- **AWS KMS**
- **AWS Organizations** : 통합된 결제를 추구
- **AWS Shield** : DDoS 공격 방지용
- **AWS WAF** : SQL Injection, XSS 방지용

### 애플리케이션

- Amazon WorkDocs
- Amazon WorkMail
- Amazon AppStream
- Amazon WorkSpaces

### 관리 도구

- -

### 분석

- **AWS Athena** : 표준 SQL을 사용하여 Amazon S3에서 직접 데이터를 분석할 수 있는 대화형 쿼리 서비스
- **AWS EMR** : 방대한 데이터를 처리하기 위한 클라우드 빅데이터 플랫폼
- **AWS CloudSearch**
- **AWS Elasticsearch Service**
- **AWS Kinesis** : 실시간으로 비디오 및 데이터 스트림을 손쉽게 수집, 처리, 분석
- **AWS Redshift** : 클라우드에서 완벽하게 관리되는 **데이터웨어하우스**(데이터를 변환해서 관리하는 DB).
- **AWS QuickSight** : 분석 보고 목적으로 사용하는 대시 보드
- **AWS Data Pipeline** : 이게 없어졌다고 들었는데 아닌가 ....
- **AWS Glue** : 분석을 위해 데이터를 쉽게 준비할 수 있도록 데이터 추출

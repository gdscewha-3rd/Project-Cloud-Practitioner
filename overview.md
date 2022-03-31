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

- Amazon CloudFront
- Amazon Route 53
- **Amazon VPC** : AWS 계정 전용 가상 네트워크
- AWS Direct Connect
- Elastic Load Balancing

### 스토리지

- **Amazon S3** : 객체 기반 스토리지. 심플하게 자주 저장하는 용도, 정적 웹사이트 호스팅 용도
- **Amazon EBS** : 블록 기반 스토리지. 영구적인 스토리지 용도.
- **Amazon EFS** : 네트워크 파일 시스템. 간단하고 확장 가능한 공유 파일 스토리지 솔루션
- **Amazon Glacier** : 아카이빙 용도. 장기 백업에 유리. Load 시에만 비용 발생
- **AWS Storage Gateway** : On-premise 데이터 스토리지를 AWS 클라우드에 연결하는 용도
- AWS Snowball

### 보안 및 자격 증명

- Amazon Inspector
- AWS Artifact
- AWS Certificate Manager
- AWS CloudHSM
- AWS Directory Service
- IAM
- AWS KMS
- AWS Organizations
- AWS Shield
- AWS WAF

### 애플리케이션

- Amazon WorkDocs
- Amazon WorkMail
- Amazon AppStream
- Amazon WorkSpaces

### 데이터베이스

- 

### 마이그레이션

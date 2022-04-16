# DevOps를 위한 다양한 AWS 서비스 소개 
[AWS Builders Standard Edition]
[Youtube](https://www.youtube.com/watch?v=pp0ew8VerRw&list=RDCMUCM9urpxJaoPf-j1cV9pGszg&index=2)

# DevOps란?

개발자의 생산성과 운영의 안정성

새로운 Application 개발 시 더 빠르게 고객에게 전달 할 수 있다. 

- `Culture`
    - ‘사고 방식’ 측면
    - 개발-운영 간의 벽을 없애준다. (개발팀, 운영팀,
    - 인프라 수명 주기를 스스로의 책임이라고 생각하게 하는 것이 DevOps의 문화임
- `Practices`
    - 서비스를 좀 더 빠르고 안정적으로 개발하기 위한, DevOps를 구현하는 주요 방식
    - 작은 단위로 자주 배포하는지, 인프라 프로세스의 자동화 , 코드 품질을 높이기 위해 사용하는 방식, 마이크로서비스 아키텍처 사용하고 있는지...
- `Tools`
    - 이를 실현시킬 수 있는 도구
    - 배포 프로세스 자동화할 도구 → CI/CD, IaC, 모니터링 및 로깅...

## 데브옵스 사례에 따른 AWS 서비스

- **CI/CD** : 코드 운영, 배포 등
    - AWS CodeCommit
    - AWS CodeBuild
    - AWS CodeDeploy
    - AWS CodePipeline
    - AWS Cloud9
- **마이크로서비스**: 하나의 큰 서비스를 작은 서비스 여러개로 분할하여 구축하는 방식
    - Amazon ECS
    - Amazon EKS
    - AWS Fargate
    - AWS Lambda
- **Infrastructure as code**: 버전 제어/지속적 통합 시 소프트웨어 개발 기법을 사용하여 인프라를 프로비저닝하고 관리하기
    - AWS CloudFormation
    - AWS OpsWorks
    - AWS Systems Manager
    - AWS CDK (Cloud Development Kit)
- **모니터링 및 로깅**: 지표와 로그를 모니터링하여 End-user에게 어떻게 영향을 미치는지 확인
    - Amazon CloudWatch
    - AWS CloudTrail
    - AWS X-Ray
    - AWS App Mesh
- **보안**: DevSecOps (규정 준수를 잘 지키는지, 위협은 없는지 확인)
    - AWS IAM (Identity and Access Management)
    - Amazon GuardDuty
    - AWS KMS (Key Management Service)
    - Amazon Inspector

---

# Infrastructure as Code (IaC)

**IaC가 왜 필요할까?** 

사람이 반복적으로 환경 구성할 때, 휴먼 에러로 문제 발생 가능. 인프라 레벨에서 발생하는 문제들을 해결하기 위해.

→ 인프라가 소스코드처럼 관리되어, 환경 내에서 버전 변경 시 정확하게 알 수 있고, 롤백도 쉬움.

![image](https://user-images.githubusercontent.com/61778930/163668273-a9d06afe-fe0f-44b0-8c0d-9f1240a5571b.png)

### AWS CloudFormation

EC2와 같은 리소스의 프로비저닝을 관리할 수 있다. 

Code→ Commit → Execute → Deploy 과정에 따라 관리

→ CloudFormation의 주요 Artifact인 Template, Change Set, Stack, StackSet를 이용하여 리소스의 프로비저닝을 관리한다. 

### AWS CDK

클라우드 인프라를 재사용 가능한 구성 요소로 모델링하기 위한 개발 프레임워크

주요 컴포넌트로는, Core Framework, AWS CDK CLI, AWS Construct Library가 있다. 

---

## AWS 개발자 도구를 사용하여 배포 자동화 (CI/CD)

### AWS CodePipeline

완전 관리형 지속적 전달 서비스 (인프라에 대한 신경을 쓸 필요가 없다)

지속적 통합/지속적 전달 워크플로우 구축 가능. 

Github이나 Jenkins와 같은 third-party 프로그램과 연동 쉬움.

### AWS CodeBuild

- 소스 코드를 컴파일하는 단계부터 테스트 실행 후, 소프트웨어 패키지를 개발하여 배포하는 단계까지 마칠 수 있는 완전 관리형 빌드 서비스

### AWS CodeDeploy

- 이전 작업분 다시 배포하는 형태로 배포 빠르게 함
- EC2, AWS Fargate, AWS Lambda, AWS ECS 등..에 적용 가능

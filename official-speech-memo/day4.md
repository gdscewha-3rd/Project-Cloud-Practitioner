# AWS IAM과 친해지기 | AWS Builders 온라인 시리즈

[Youtube](https://www.youtube.com/watch?v=c70glL9Znzs)

---

IAM은 AWS 사용자라면 끊임없이 사용하게 되는 아주 중요한 요소이다. AWS 리소스를 사용하기 위한 모든 요청은 Identity and Access Management, 즉 IAM을 통해 이루어진다.

따라서 IAM은 가장 기본적이면서도 핵심적인 도구이며, 사용자의 보안을 위해 꼭 알아야 하는 요소이다.

![https://blog.kakaocdn.net/dn/63fTd/btrAyMF7yuQ/sxPs5WiyPJxOQfXkYKuRfK/img.png](https://blog.kakaocdn.net/dn/63fTd/btrAyMF7yuQ/sxPs5WiyPJxOQfXkYKuRfK/img.png)

## IAM 이란?

Identity and Access Management 으로, AWS 전체의 권한 통제 시스템이다.

### ***Root Account vs IAM*** 어떤 걸로 로그인 해야 할까?

루트 어카운트는 거의 모든 권한을 가지고 있기 때문에 AWS 작업을 이 계정으로 하는 것은 보안에 좋지 않다. 루트 어카운트보단 IAM 유저를 만들고 이를 통해 로그인 하는 것이 권장된다.

IAM 계정으로 모든 접근이 가능하며, Root 계정을 사용해야만 하는 상황은 1)처음 계정을 만들 때와 2)첫 번째 IAM 유저를 생성할 때 이 2가지 상황뿐이다.

## IAM 사용 방법

사용자가 IAM을 어떻게 사용할 수 있을까? 아래 그림과 같이 4가지 방법이 있다.

Low에서 High 레벨로 갈 수록 인프라 관리가 코드화됨으로써 대규모 서비스에도 적용이 쉬워진다.

![https://blog.kakaocdn.net/dn/4GKpE/btrAwDWuS49/F2bXWJ1nxyPaV1jGITwTc1/img.png](https://blog.kakaocdn.net/dn/4GKpE/btrAwDWuS49/F2bXWJ1nxyPaV1jGITwTc1/img.png)

**1. Console창을 이용해 수작업으로 관리**하는 방법. (Low level)AWS 콘솔창을 이용하는 방법으로, 기본 사용자들이 제일 많이 하는 손쉬운 방법이다.편리하다. 반복 작업을 하기에는 한계가 있다.

**2. Script 기반 작업**스크립트를 짜서 리소스를 관리한다. 반복 작업은 조금 쉬워지겠지만, 큰 규모로 리소스 다룰 때 적합하지 않다.

**3. 프로비저닝 엔진을 사용하기**Infra as a Code (IaC) 라고도 함. 코드를 통해서 인프라를 관리하자.오픈소스를 이용해서 환경을 자동으로 배포하거나 복제가 가능하다.

**4. CDK 사용하기**내가 원하는 언어를 통해서 인프라를 관리하자. (TS, JS, C#, Java, Python...)이를 Cloud Development Kit (CDK)라고 함.

---

그래서 IAM은 무슨 일을 할까? **I** 와 **AM** 으로 나누어서 살펴보자.

## **I** (Identity)가 하는 일

### IAM User: 콘솔 로그인용

로그인 시 루트 유저는 너무 많은 권한을 보유하고 있어 보안에 취약하다. IAM User를 만들어 콘솔에 접근하자.

### IAM Role: API 호출 시 사용하는 권한(역할).

IAM User가 AWS 서비스 제어를 할 때 사용자 권한을 임시로 부여 받는다. 사용자 권한을 Role(역할)로 부여해둠으로써 매번 권한 부여를 할 필요가 없어진다.일정 시간이 지나면 만료되는 임시 자격증명 Token을 사용해서, 안전하고 편리하게 사용한다. 이를 Assume 한다고 한다.

외부 사용자와 AWS 서비스를 연결해주는 등, 매핑이 가능하고, 다른 AWS 어카운트에 접근하는 것도 가능해 유용하다.

## **AM** (Access Management)가 하는 일

어떤 리소스에 대해 "어떤 권한을 가지는가"를 체크하는 도구.

### ****Policy**:** JSON 포맷으로 Deny/Allow를 명시해두는 정책.

```
{
"Statement" :[{
		"Effect":"Allow or Deny",
        "Principal":"principal",
        "Action":"action",
        "Resource":"arn",
        "Condition": {
        	"condition":{
            	"key":"value" }
        	}
        }
	]
}
```

위는 Policy의 예시이다. Policy 구조에 대해 더 알아보자면,

**E**ffect: 명시된 정책에 대한 허용/차단

**P**rincipal: 접근을 허용/차단하고자 하는 대상*"Principal":"AWS":"arn:aws:iam::123456789012:user/username"*

**A**ction: 허용/차단하고자 하는 접근 타입*"Action":"s3:GetObject"*

**R**esource: 요청의 목적지가 되는 서비스*"Resource":"arn:aws:sqs:us-west-2:123456789012:queue1"*

**C**ondition: 명시된 조건, 유효하다고 판단될 수 있는 조건*"StringEqualsIfExists":{"aws:RequestTag/project": ["Pickles"]}*

### Policy를 어떻게 사용할까? 예제를 통해 살펴보자.

![https://blog.kakaocdn.net/dn/lGx71/btrAxHZBiDZ/4JafQzkbKI9KpK3ml7YL9k/img.png](https://blog.kakaocdn.net/dn/lGx71/btrAxHZBiDZ/4JafQzkbKI9KpK3ml7YL9k/img.png)

상황

EC2 인스턴스에 IAM role이 부여되어 있고, DynamoDB에 접근해 Read/write 작업을 하려고 한다.

이때 이 IAM 정책은 어떤 조건을 갖고 있어야 할까?

![https://blog.kakaocdn.net/dn/co3Kyr/btrAAbFofbN/CX8UsBcADuJ7pvecfuNpP1/img.png](https://blog.kakaocdn.net/dn/co3Kyr/btrAAbFofbN/CX8UsBcADuJ7pvecfuNpP1/img.png)

1번째 정책

먼저 위와 같이, 모든 Action, Resource에 대해 접근을 allow 하는 방법이 있다.

접근은 가능해지겠지만, 이와 같은 정책은 거의 루트 유저와 같은 정책으로 너무 많은 권한을 부여해주기 때문에 위험하다. 더 Least privilege 한 정책으로 세분화 해보자.

![https://blog.kakaocdn.net/dn/nLuTL/btrzq6LYxA7/r7QfMx2DZfQPAnH88mI0HK/img.png](https://blog.kakaocdn.net/dn/nLuTL/btrzq6LYxA7/r7QfMx2DZfQPAnH88mI0HK/img.png)

2번째 정책 (액션 구체화)

액션을 좀 더 세분화했다. DB에 Get/Put 하는 작업만 가능하도록 구체적인 액션을 설정했다.

1번 정책보다는 안전하지만, 그래도 아직 리소스가 '모두'로 설정되어 있어서 조금 더 개선의 여지가 있다.

![https://blog.kakaocdn.net/dn/beDM2K/btrAzvKShkK/lPSQ91KL4oM5yC7jhLBgU1/img.png](https://blog.kakaocdn.net/dn/beDM2K/btrAzvKShkK/lPSQ91KL4oM5yC7jhLBgU1/img.png)

3번째 정책(리소스 구체화)

리소스도 위와 같이 구체화 할 수 있다. 정확히 어떤 DB인지, 특정 DynamoDB 리소스를 지목해 설정해주자.

해당 리소스 외에 다른 db 객체에는 IAM 유저가 접근할 수 없어져 보다 안전하다.

![https://blog.kakaocdn.net/dn/dpwPXv/btrAxmnuChD/3zkTgKCXp2aJQhNLqlLJZK/img.png](https://blog.kakaocdn.net/dn/dpwPXv/btrAxmnuChD/3zkTgKCXp2aJQhNLqlLJZK/img.png)

4번째 정책 (특정 조건 설정) -> Good :)

한 걸음 더 나아가 특정 조건을 추가할 수 있다. 위의 Condition 처럼, IP 주소나 소스 IP를 설정해줄 수 있는데,

사무실 NAT IP 같은 것들을 이런 IAM 정책 조건으로 정의하게 되면, 회사 네트워크 외부에서는 임의 요청을 할 수 없도록 구성할 수 있게 되는 것이다.

이외에도 굉장히 다양한 조건들을 설정할 수 있다.

![https://blog.kakaocdn.net/dn/bLiUaL/btrAs93kidt/WGBu73hbtVrEHdS2K4ccrk/img.png](https://blog.kakaocdn.net/dn/bLiUaL/btrAs93kidt/WGBu73hbtVrEHdS2K4ccrk/img.png)

IAM 정책 종류

위와 같이 다양한 정책 종류가 있다. 가장 많이 사용되는 정책은 Identity-based와 Resource-based 정책이다.

---

### IAM 모범 사례

IAM이 익숙하지 않은 사람(=나)을 위해 모범 사례를 살펴보며 IAM과 친해져보자.

### 모범 사례 key point를 정리하자면,

- root 계정은 제대로 보호하자. 그리고 모든 작업은 IAM으로 진행하자.루트 계정 액세스 키 페어는 아예 삭제하거나 잠금 설정 하는 것이 좋다. 루트 계정이나 권한 있는 사용자에 대해 MFA 인증 체계를 활성화하는 것도 Best!
- 반드시 실제 사용자와 IAM 유저를 **1:1 매핑**해주어야 한다. (개별 IAM 사용자 만들기)다수의 사용자가 하나의 IAM을 만들어 사용하지 말 것. **그룹**을 사용해 IAM 사용자에게 권한을 할당할 수도 있다.
- 정책은 꼭 필요한 권한만 허용해주는 **최소 권한 부여의 원칙**이 중요하다. 이 때 활용할 수 있는 서비스로 **IAM Access Advisor** 가 있다.주기적으로 감사하거나 자동화하는 노력이 필요하다.
- 서비스 간 권한 제어에 **Role**을 적극 사용하자.Role을 사용하여 권한을 위임할 수도 있어서 편리하다.예를 들어, B어카운트에 A어카운트가 정책을 assume 할 수 있게 신뢰 정책을 설정해두면 서비스 간에 훨씬 안전하게 접근을 구성할 수 있게 된다.

![https://blog.kakaocdn.net/dn/bd1XXO/btrAvGmTdZl/knQANAe6OLNwKUVERSg0r1/img.png](https://blog.kakaocdn.net/dn/bd1XXO/btrAvGmTdZl/knQANAe6OLNwKUVERSg0r1/img.png)

- IAM 자격증명을 정기적으로 교체하자. **IAM Credential Report**를 활용해서 교체 주기가 지난 IAM 을 확인하거나 다양한 통계를 확인할 수 있다.
- 보안 강화를 위해 정책 조건(Policy)를 잘 정해주자.필요한 상황에 맞추어 정책을 설정해주면 큰 도움이 된다.
- IAM 활동을 모니터링하고 감시하자. 이때 사용할 수 있는 서비스로는 **AWS CloudTrail, AWS IAM Access Analyzer, Amazon GuardDuty, AWS Security Hub** 등이 있다.

더 자세한 모범사례는 [Official docs](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)를 참고하자.

---

여기까지 AWS에서 IAM이 어떤 역할을 하는지, 정책의 구조와 종류를 살펴보고 모범사례를 살펴보았다.

IAM은 AWS를 제대로 사용하려면 꼭 알아야 하는 서비스라고 생각한다.

잘 공부해서 안전하게 클라우드 서비스를 이용해야겠다.

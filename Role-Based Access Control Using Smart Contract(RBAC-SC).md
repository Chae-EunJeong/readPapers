# Role-Based Access Control Using Smart Contract(RBAC-SC)
![rbac-sc](https://user-images.githubusercontent.com/32332719/68259889-76f70180-007e-11ea-8d42-c0eadb979bbe.PNG)
- Role Issuer가 trans-organizational한 방식에서 smart contract를 통해 사용자의 역할을 소유하고 관리하는 접근 제어 방법
# Problem statement
- trans-organizational 방식에서 role을 이용할 때 role에 대한 인증이 중요하다. 
- trans-organizational 방식에서 role을 사용해 접근 제어를 할 때, offline에서는 role에 대한 검증이 어렵지 않지만 computer network에서는 role에 대한 검증이 명백하지 않다.
- trans-organizational한 방식에서도 효율적이고 안전한 role 기반 접근 제어를 하는 방법이 필요하다.
# RBAC-SC composed of
## 1. smart contract
- user를 추가하고 user에 대한 관리를 할 때 사용한다.
### Role Issuer
- EPK라는 개인키와 EOA라는 공개키 보유
- 사용자의 추가 및 제거, 보증인의 추가 및 제거의 기능을 하는 스마트 컨트랙트를 생성한다.
- 스마트 컨트랙트의 주소, 공개키, interface를 Ethereum blockchain을 통해 발행하여 public하게 만든다.
## 2. challenge-response protocol
- user가 service-provider에 인증을 하고 검증을 받을 때 사용되는 프로토콜이다. 
### User  
- user도 EPK라는 개인키와 EOA라는 공개키 보유
### User 인증 방법
- service-provider에게 공개키 EOA를 보내면, 
- service-provider가 role issuer이 발행한 smart contract로 정보 확인  
- challenge를 user로 보내면 user는 EPK를 이용한 서명을 response로 보내서 service-provider가 역할 검증

# Reference
CRUZ, Jason Paul; KAJI, Yuichi; YANAI, Naoto. RBAC-SC: Role-based access control using smart contract. IEEE Access, 2018, 6: 12240-12251.

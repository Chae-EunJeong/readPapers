# Data Sharing System Integrating Access Control Mechanism using Blockchain-Based Smart Contracts for IoT Devices
![캡처](https://user-images.githubusercontent.com/68576770/89714254-4e6ab200-d9d8-11ea-8d67-19a39a9aff41.PNG)
- data sharing and access control system between IoT devices to achieve trustfulness, authorization and authentication using smart contracts
# Problem Statement
- growth of the IoT networks results in many challenges such as illegitimate data sharing, unauthorized access control, unauthenticated users, single point of failure due to centralization, etc.
- for interacting between IoT devices, the blockchain-based system need to achieve:
  - trustfulness and authentication for data sharing 
  - authorization and privileged for access control
 # Proposed System Model Using Smart Contracts
 ### 1. ACC(Access Control Contract)
- main smart contract which manages overall access control of the system
  - ACC executed when a subject sends service request
  - after registration, ACC forwards the request of subject to the object by checking corresponding permission level
- access control, efficient and less cost consumption
  - a single smart contract that manages the service sharing among users(not created for each transaction)

 ### 2. RC(Register Contract)
- registers authenticate users and maintains the registration table
- authentication and verification
  - registers user who becomes part of the system
  - maintain records in the user registration table
  ![image](https://user-images.githubusercontent.com/68576770/89714984-5842e400-d9dd-11ea-9260-1cba7bf2ba12.png)

 ### 3. JC(Judge Contract)
- judges the behavior of users and determines penalty for misbehavior or checks permission levels
- trustfulness : only trusted users are allowed to access their required services
- misbehaviors conducted by the subject are:
  - subject sends frequent and too many requests
  - subject cancels its generated request
- 1. after misbehavior, corresponding penalty is determined then, state of subject halted and subject cannot send requests for a certain time period
  - ![image](https://user-images.githubusercontent.com/68576770/89715326-e5873800-d9df-11ea-9efa-47106108338c.png)
- 2. if no misbehavior, permision levels are checked
  - ![image](https://user-images.githubusercontent.com/68576770/89715373-4747a200-d9e0-11ea-9d69-6525f1a1fd7a.png)

# Reference
Sultana, Tanzeela, et al. "Data sharing system integrating access control mechanism using blockchain-based smart contracts for IoT devices." Applied Sciences 10.2 (2020): 488.

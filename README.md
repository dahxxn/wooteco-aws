# wooteco-aws
AWS 배포 학습 저장소

## 산출물 
### 배포 서비스 

| 항목 | 내용 |
|---|---|
| 서비스 접속 주소 | [방탈출 예약 서비스 바로가기](http://ec2-3-36-106-35.ap-northeast-2.compute.amazonaws.com:8080/) |
| 배포 환경 | AWS EC2 |
| 애플리케이션 | Spring Boot |

### 보드게임 완주 여권

| 응답 패킷 관점 | 요청 패킷 관점 |
|---|---|
|<img width="5712" height="3213" alt="IMG_9889" src="https://github.com/user-attachments/assets/cf455d5b-83a0-4d76-b502-1aa99f94b2c3" />|<img width="5712" height="3213" alt="IMG_9888" src="https://github.com/user-attachments/assets/06871823-6e84-4653-acd6-983a078538a4" />|

### AWS 네트워크 구성도

```mermaid
flowchart TD

    User["사용자 브라우저"]

    User -->|"HTTP :8080"| IGW["Internet Gateway<br/>igw-*********"]

    subgraph VPC["VPC<br/>TECHCOURSE-LV2"]
        RT["Route Table<br/>192.168.0.0/16 → local<br/>0.0.0.0/0 → Internet Gateway"]

        subgraph PublicSubnet["Public Subnet<br/>techcourse-lv2-public"]
            SG["Security Group<br/>techcourse-lv2-public"]
            EC2["EC2<br/>ec2-handa"]
            APP["Spring Boot Application<br/>Port 8080"]
        end
    end

    IGW --> RT
    RT --> SG
    SG --> EC2
    EC2 --> APP
```

# skt_HealthCheckup_Guide
<br>

![image](https://user-images.githubusercontent.com/102462534/181045821-19486c99-4c4a-4c4b-91b0-1795cc6983e4.png)


> SKT의 NUGU AI 스피커를 활용한 건강검진 가이드 앱 제작 프로젝트

<br>

이 프로젝트는 SKT와 함께하는 인재양성 교육을 통해 진행되었습니다.<br>
프로젝트의 참여인원은 이호성, 이준형, 강지윤, 김지헌입니다. 팀의 기획자로 참여하였습니다.

<br/>

#### :bulb: 프로젝트 주제 : SKT NUGU AI Speaker 음성인식을 기반으로 한 건강검진 가이드 앱 제작
#### 📆 프로젝트 구현 기간 : 2020년 09월 28일 ~ 2020년 11월 26일
#### 🦉 서비스 제공 스펙 
|서비스 분류|제공 경로|상세 내용
|-|-|-|
| 디바이스 | 알버트 AI | NUGU 앱에서 확인 |
| Voice AI cloud | SKT TTS |  기본: 한국 여자 20 ~ 30세 목소리 |
| 제공 플랫폼 | Nugu APP | Nugu Play - 정보/생활 |
| 지역과 시간대 | 국내 | GMT 9:00 |
| 특정 IP (어뷰징) 제한 | 알버트 AI/ Nugu 스피커 유입 | 없음 |

<br>
<br>

#### 🛠 기술 스택
- Python
- AWS - EC2
- Python3 Flask

#### 💻 개발 환경 및 툴
- windows
- Pycharm
- vim
- SKT NUGU developers
- Slack

<br>
<br>

--------------------
<br>

## 1. 건강검진 가이드 앱 기능
건강검진 가이드 앱은 3개의 주요 기능을 가지고 있습니다. <br>
1. 건강검진 관련 발화에 대한 처리 (ex. 폐암 건진에 대해 알려줘)
2. 생년월일과 성별에 해당되는 건강검진 여부 안내 (ex. 1995년 10월 23일생 남자에 대한 건강검진 알려줘)
3. 건강검진에 대한 주의사항 안내 (ex. 건강검진에서 주의할 사항은 뭐야?)


<br>

> 건강검진 가이드 서비스의 flow chart는 다음과 같습니다.

![image](https://user-images.githubusercontent.com/102462534/181048346-fba15b77-4f37-4e3e-8964-f33002da715d.png)

<br>

> 각 기능에 대한 대화 로직 및 응답 설계는 다음과 같습니다.
<br>

건강검진 상세 질문  |   사용자의 정보에 따른 건강검진
:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/102462534/181048640-fb9921e4-d9a0-42ee-a0a7-676d9a5ca17f.png) | ![image](https://user-images.githubusercontent.com/102462534/181048707-cafbb9b6-a2e3-43b2-af66-3ab717f94ddf.png)




<br>

<br>
<br>

--------------

<br>

### 2. Nugu Play 앱 구조
- Nugu Play의 구조는 다음과 같습니다.
<br>

![image](https://user-images.githubusercontent.com/102462534/181048983-283bf5b6-7ab7-4672-ac76-df4ccdb8bfa0.png)

<br>
<br>

--------------------

<br>

### 3. API 서버 구현
Python3 Flask를 이용한 API 서버를 구현하였습니다. github를 통해 관리되는 소스코드는 Nugu play에서 사용하기 위한 API 서버 및 DB 관련 코드입니다. 웹서버는 아마존 AWS에서 Flask를 통해 동작합니다. Nugu play로부터 정의된 요청(POST방식)이 오면, 그에 대한 응답을 json형태로 반환하게 됩니다.



<br>
<br>

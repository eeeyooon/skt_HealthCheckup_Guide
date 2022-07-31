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



### 👨🏻‍🔧 Nugu Developers

NUGU developers는 SK텔레콤이 보유한 최고 수준의 음성 인식, 음성 합성, 자연어 이해 등의 기술력을 기반으로 NUGU 혹은 제휴사의 디바이스와 앱 사용자에게 AI 서비스를 제공할 수 있는 플랫폼입니다. NUGU 플랫폼 기반의 AI 서비스를 편리하게 개발할 수 있도록 다양한 Tool과 개발 문서를 제공합니다.

**NUGU play kit**는 NUGU 플랫폼에서 동작하는 AI 서비스의 단위인 NUGU play를 만들고 관리 수 있도록 서비스 사업자나 개인 개발자를 위해 제공하는 툴입니다. **NUGU play kit**는 간단한 코드 정의와 예시 문장 입력만으로 손쉽게 NUGU play를 만들 수 있는 Play Builder와 생성한 NUGU play를 관리, 배포하고 사용 통계를 조회할 수 있는 콘솔로 구성되어 있습니다. 
<br>


**Nugu Play Builder**는 NUGU play를 생성하는 개발 도구로 이용자의 발화를 이해하는 User Utterance Model, 이를 기반으로 기능을 수행하는 Action을 조합하여 하나의 완결된 Play를 생성합니다.

![image](https://user-images.githubusercontent.com/102462534/182028700-03a59aff-40d6-4864-9614-9c2a93697746.png)


**Backend Proxy** : 외부 서버를 호출하여 대화 관리자에서 정보를 전달하는 서버 

- 외부 서버로부터 정보를 가져와야 하는 경우
- 사칙 연산, 날짜/시간 계산 등 로직을 통해 정보를 가공해야 하는 경우
- 시나리오 전체에 필요한 정보를 미리 가져와야 하는 경우

![image](https://user-images.githubusercontent.com/102462534/182028678-539691be-e48c-4f47-a36f-5002e1b6f55e.png)


<br>
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

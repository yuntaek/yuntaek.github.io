---
layout: post
title:  "CJ Onstyle - Shorform GEN AI Workshop"
date:   2024-07-02 10:11:44 +0900
categories: AWS CJOnstyle
---
<img src="/img/aws-background.png" alt="aws Logo" width="100%"><br>

## Location

- 18층 100호 화랑도

---

## Time Table

| At Time | Seesion | Session Agendat | Speaker | Seesion 자료 |
| ----- | ------ | ------ | ------ | ------ |
| 01:00PM - 03:00PM | GenAI-Cldue3 | Prompt Engineering | SA 임윤택 <br/> SA 이상욱 | |
| 03:00PM - 05:00PM | Shortform | shortform enablement | SA  기철민 | |


# Gen-AI Claude3 Hands-On 안내

## workshop link
-  김지휘 : [https://catalog.us-east-1.prod.workshops.aws/join?access-code=dbc1-1977fb-8f](https://catalog.us-east-1.prod.workshops.aws/join?access-code=dbc1-1977fb-8f)
-  송진호 : [https://catalog.us-east-1.prod.workshops.aws/join?access-code=9b9e-179d91-d3](https://catalog.us-east-1.prod.workshops.aws/join?access-code=9b9e-179d91-d3)
-  김채원 : [https://catalog.us-east-1.prod.workshops.aws/join?access-code=0cd2-163cbf-b9](https://catalog.us-east-1.prod.workshops.aws/join?access-code=0cd2-163cbf-b9)
- 현훈범 : [https://catalog.us-east-1.prod.workshops.aws/join?access-code=df02-1a7d2b-29](https://catalog.us-east-1.prod.workshops.aws/join?access-code=df02-1a7d2b-29)
- 신영화 : [https://catalog.us-east-1.prod.workshops.aws/join?access-code=e544-17ecb1-3d](https://catalog.us-east-1.prod.workshops.aws/join?access-code=e544-17ecb1-3d)
- 성홍규 : [https://catalog.us-east-1.prod.workshops.aws/join?access-code=3732-1e359c-6f](https://catalog.us-east-1.prod.workshops.aws/join?access-code=3732-1e359c-6f)

## console 접근방법

1. 각 사용자별로 지정된 링크를 이용해서 워크샵 스튜디오에 로그인 합니다.

3. 이 이벤트와 관련된 약관을 주의 깊게 검토한 후, **Join event**를 클릭하세요.
![joinevent](/img/joinevent.png)

4. 이벤트에 가입한 후, 이벤트 정보와 워크샵 세부 사항이 있는 페이지를 볼 수 있습니다. 왼쪽 탐색 창에서 **AWS account access** 섹션도 볼 수 있습니다. 이 옵션을 사용하여 제공된 임시 AWS 계정에 접근할 수 있습니다.
![AWSAccess](/img/awsaccess.png)

5. **Open AWS console** 링크를 통해 AWS 관리 콘솔 홈페이지를 열 수 있습니다. 이는 각 서비스에 접근할 수 있는 표준 AWS 콘솔입니다. 워크샵 인프라는 특정 리전에 배포되므로 해당 리전에서만 접근할 수 있습니다.

---

## bedrock model Access

2. Model access 화면에서 오른쪽 상단 버튼 **"Enable specific models"** 를 클릭합니다:
![모델 액세스](/img/modelaccess_1.png)

3. Model access 화면에서 **다음 모델만 선택** 하고 **"Next"** 버튼을 클릭합니다:
  - Anthropic
    - Claude 3 Sonnet
    - Claude 3 Haiku
![모델 액세스 요청](/img/modelaccess_2.png)

4. 모델 요청 내용을 리뷰하고 **"Submit"** 버튼을 클릭합니다![모델 리뷰](/img/modelaccess_3.png)
설정이 완료되었습니다. lessons로 진행해 주세요.

⌛ 모델 액세스 프로세스가 완료되기까지 **최대 5분** 정도 걸릴 수 있습니다. ⌛

---

## sagemaker notebook instance 설정

1. Amazon SageMaker를 search 창에 입력하고, 해당 서비스 콘솔창으로 이동합니다.
![sagemaker1](/img/SearchSageMaker.jpg)

2. 왼쪽 패널에 있는 nootbook을 선택하여 미리 설치된 Notebook Instances **"PromptEngWithAntoropicNotebook"** 을 목록에서 확인합니다. Actions의 **Open JupyterLab** 을 눌러서 실행합니다.
![notebook](/img/sagemaker_3.png)

3. 노브북 인스턴스에서 최상단 root로 이동합니다.
![](/img/moveToRoot.png)

4. 이전에 설치된 rpository를 삭제합니다.
![](/img/deleteFiles.png)

5. 새로 repository로 clone 하기위해 **"Git Clone"** 버튼을 클릭합니다. 
![](/img/cloneRepo_1.png)

6. 팝업창의 "https:/github.com/yuntaek/prompt-engineering-with-anthropic-claude-v-3.git" 해당 repository 주소를 입력하여 "clone"버튼을 누릅니다.
![](/img/cloneRepor_2.png)

7. 왼쪽 "Git" Icon을 누룹니다.
![](/img/changeBranch_1.png)

8. Branch를 oringin/kr로 변경합니다.
![](/img/changeBranch_2.png)

9. current Brach가 kr인것을 확인합니다.
![](/img/changeBranch_3.png)

10. 파일 브라우저 버튼을 눌러 필요한 노트북을 실행시킵니다.
![](/img/readyToWorkshop.png)

# Shortform Hands-On 안내

# 피드팩
URL : [https:/pulse.aws/survey/4SQC9PFY](https:/pulse.aws/survey/4SQC9PFY) <br/>

<img src="/img/QRCode.png" alt="QRCODE SA" width="200" >
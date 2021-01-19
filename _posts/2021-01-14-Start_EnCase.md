---
title: EnCase(1) - 케이스 생성 후 증거 파일 추가하기
comments: true
author: Present4n6
categories: [DigitalForensics,EnCase]
date: 2021-01-13 22:02:00 +0900
tags: [DigitalForensics,EnCase]
math: true
---

## **EnCase?**  

디지털포렌식을 수행할 때 사용하는 툴로 가장 널리 알려진 프로그램 중 하나인 <kbd>EnCase</kbd>에 대해서 포스팅을 해보겠습니다. EnCase는 **`OpenText`**사(구 Guidance Software)에서 제공하는 프로그램입니다. 꽤 오래전부터 디지털포렌식 업무에 사용이 되어왔는데요, 미국 법정에서 EnCase를 사용해서 확보한 디지털 증거를 많이 채택해왔기 때문에 공신력 있는 프로그램으로 평가를 받고 있습니다. 요즘은 **`Magnet Forensics`**사의 <kbd>AXIOM</kbd>, **`Nuix`**사의 <kbd>NUIX</kbd> 등 뛰어난 프로그램들이 많이 있어서 입지가 줄어들긴 했지만요.  
저도 EnCase를 깊게 사용해보지는 않았습니다만 디스크 이미지를 분석하는데 유용하게 사용할 수 있으며 EnScript라는 프로그래밍 기능을 제공하여 정말 다양한 기능을 사용할 수 있다고 알고 있습니다. 그리고 <kbd>EnCE</kbd>라는 EnCase 전용 자격증도 있을 정도이죠.  
이렇게 좋은 프로그램이지만 정말 아쉬운 점은 일반인은 사용하기가 어렵다는 점입니다. 가격이 너무비싸서 사용하기가 어려운데요, EnCase를 사용하기 위해서는 무려 천 만원이 넘는 가격을 지불하고 동글키를 얻어야 사용을 할 수 있습니다.  
저는 BoB에서 EnCase를 사용해볼 수 있었습니다. BoB에서는 EnCase 정품을 가지고 있으며 EnCase에 대한 교육도 진행을 하기 때문에 BoB 활동을 하면서 많이 배울 수 있었습니다. BoB를 안 해보신 분들은 BoB에 꼭 지원해서 질 좋은 교육과 많은 경험을 해보셨으면 좋겠습니다.    
BoB 활동을 하면서 배웠던 EnCase의 기능들을 블로그에 정리를 해볼려고 합니다. 제가 EnCase의 모든 것을 배운것은 아니기 때문에 배웠던 내용들 중 일부분에 한해서 포스팅을 해볼려고 합니다. 이번 포스팅에서는 간단하게 EnCase의 화면구성이 어떻게 되어 있는지 살펴보고, 케이스를 생성하고 증거 파일을 추가하는 것까지 진행을 해보겠습니다.  


* * *  

## **EnCase 맛보기**  
### **1. EnCase 실행**

`EnCase Version : EnCase Forensic Training v20.2`

* EnCase를 실행하면 아래와 같은 화면을 볼 수 있습니다. 최근에 사용했던 Case 목록을 보여주고 새로운 case를 생성할 수 있는 목록이 있습니다. 케이스를 새로 생성하기 위해 New Case를 선택해줍니다.

![upload-image](/assets/post/EnCase/1.png)  

### **2. Case 생성하기**

* New Case를 하면 아래 그림과 같이 Case의 정보를 설정할 수 있습니다. 좌측에 보면 자주 사용하는 Case의 템플릿을 불러올 수도 있고 새로 생성할 수도 있습니다. 우측에는 Case의 이름, 경로 등을 지정해줄 수 있습니다. 또한 백업 옵션도 지정해줄 수가 있는데요. 백업 옵션을 지정하면 용량을 많이 차지하기 때문에 연습할 때는 끄고 진행을 하겠습니다. 현업에서는 당연히 체크를 하고 진행을 하겠죠?  
Case를 생성하는데는 간단하게 이름, 경로, 백업 여부 정도만 지정해주면 됩니다.    

![upload-image](/assets/post/EnCase/2.png) 

### **3. 증거 파일 추가하기**

* Case 생성을 정상적으로 완료했다면 아래 화면을 볼 수 있을 것입니다. 그림을 보면 크게 **Search, Browse, Evidence, Report, Case**로 항목이 나뉘어져있습니다. 증거 파일을 추가하기 위해 **`Evidence`** 항목의 **`Add Evidence`**를 선택해줍니다.

|---|---|
Search|검색기능을 수행했을 때 그 결과를 확인할 수 있는 메뉴를 포함하고 있습니다.  
Browse|올라간 증거 파일의 내부 구조를 확인하고 분석할 수 있는 창을 열 수 있으며, EnScript를 작성할 수 있는 메뉴를 포함하고 있습니다.  
Evidence|증거 파일을 추가할 수 있고, Process Manager라는 분석 기능을 제공하고 있습니다.  
Report|EnCase에서 제공해주는 보고서 작성 기능에 대한 메뉴를 포함하고 있습니다.  
Case|설정한 Case의 옵션을 변경하거나 변경된 정보를 저장하는 메뉴를 포함하고 있습니다. 

![upload-image](/assets/post/EnCase/3.png)  

* Add Evidence를 누르면 아래 화면을 볼 수 있습니다. 제가 올릴 이미지 파일은 **`EVF 파일`**(EnCase 이미지 파일 포맷)이기 때문에 **`Add Evidence File`**을 선택하고 마운트할 이미지 파일을 선택해줍니다.  

![upload-image](/assets/post/EnCase/4.png) 
![upload-image](/assets/post/EnCase/5.png)


### **4. 화면구성 살펴보기**

* 증거 파일을 올리면 아래 그림처럼 보기만해도 굉장히 복잡해보이는 화면이 나옵니다. 화면에 보이는 내용으로는 이미지 파일의 경로, GUID 값, 무결성 검증 결과 등이 보이고 하단의 Fields 영역에서도 이미지 파일의 해시값, 압축률, 저장매체 정보, 쓰기 방지 정보, 드라이브 타입 등 이미징 할 때 설정한 값과 저장매체의 정보를 확인할 수 있습니다. 또한 Report 탭을 누르게 되면 정보들을 아래와 같이 보기 좋은 형태로 확인할 수 있습니다.  
증거 파일을 디스크 구조로 확인하려면 Name 부분을 클릭하면 됩니다.  


![upload-image](/assets/post/EnCase/6.png)
![upload-image](/assets/post/EnCase/7.png)

* EnCase의 분석화면은 아래 그림과 같이 크게 4가지 화면으로 구성이 되어 있습니다.  

|---|---|
Tree Pane|디스크 브라우징 기능을 통해 디스크의 데이터를 트리 구조로 보여줍니다.  
Table Pane|파일의 타임스탬프 값, 해시 값, 파일 크기, 섹터 위치 등의 정보를 보여줍니다.
View Pane|이미지 파일에 대한 정보를 볼 수 있습니다. 또한 선택한 파일의 Hex값을 볼 수 있으며 데이터 뷰잉 기능을 통해 파일의 형태 등을 보여줍니다.
Filter/EnScript Pane|필터 기능을 통해 원하는 결과물만 볼 수 있으며 EnScript를 적용할 수 있습니다.  

![upload-image](/assets/post/EnCase/8.png)


EnCase 프로그램을 사용해서 케이스를 생성하고 증거 이미지 파일을 올려보는 것까지 해보았습니다. 이제 분석을 시작하기 위한 재료준비가 완료된 것 같네요. 다음에는 분석을 진행하면서 사용할 수 있는 기능에 대해서 포스팅을 해보도록 하겠습니다.  
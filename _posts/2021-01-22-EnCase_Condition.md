---
title: EnCase(4) - Condition 다루기
comments: true
author: Present4n6
categories: [DigitalForensics,EnCase]
date: 2021-01-22 18:06:00 +0900
tags: [DigitalForensics,EnCase]
math: true
---
## **EnCase에서 Hash 구하기**  

이번 포스팅에서는 EnCase에서 제공해주는 기능 중 하나인 <kbd>Condition</kbd>를 사용하는 방법에 대해 알아보도록 하겠습니다.  


### **1. Condition**

* EnCase의 화면 구성에서 하단의 **`Filter/EnScript Pane`**에 보면 **`Conditions`**라는 것이 있습니다. 이는 파일에 대해 조건문을 수행한다고 보면 되겠습니다. 컨디션은 기본적으로 EnCase에서 제공해주는 것이 있고 사용자가 직접 만들어서 사용할 수도 있습니다. 이번 포스팅에서는 사용자가 만드는 방법에 대해 알아보겠습니다.  

![upload-image](/assets/post/EnCase/47.png)  

* 위의 그림에서 **`Users`** 폴더를 선택하고 New를 눌러 새로운 컨디션을 생성해야 합니다. 그러면 아래 그림과 같은 창이 뜨게 되는데 컨디션을 저장할 경로를 지정해주고 **`if New`**를 선택해줍니다.  

![upload-image](/assets/post/EnCase/48.png)  

* 여러가지 목록 중에서 자신이 필요한 기능을 선택합니다. 저는 jpg 파일만 골라서 보는 기능을 만들기 위해 **`File Ext`**를 고르고 연산자는 **`Matches`**로 일치하는 값들만 뽑을 수 있도록 지정하겠습니다. 그리고 **`Value`**에는 jpg라고 입력을 해주었습니다.  

![upload-image](/assets/post/EnCase/49.png)  

* 함수하나를 추가해주면 아래 그림과 같이 적용된 것을 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/50.png)  

* 또한 **`Source Code`**탭에 가보면 지정해준 함수가 EnScript 형태로 표현이되어 있는 것을 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/51.png)  

* 생성한 컨디션을 실행하기 위해서는 컨디션의 이름을 더블 클릭하면 됩니다. 그리고 옵션을 지정해주고 OK를 선택하면 됩니다.  

![upload-image](/assets/post/EnCase/52.png)  


* 실행결과는 다음과 같이 JPG 파일만 뽑힌것을 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/53.png)  


이번 포스팅에서는 간단하게 EnCase의 <kbd>Condition</kbd>을 생성하고 사용하는 방법에 대해서 간단하게 알아봤습니다. 사용자가 원하는 기능을 간단하게 구현을 할 수 있다는 점에서 상당히 좋은 기능인 것 같습니다.







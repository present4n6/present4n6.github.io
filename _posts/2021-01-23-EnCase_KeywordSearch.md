---
title: EnCase(5) - Keyword 다루기
comments: true
author: Present4n6
categories: [DigitalForensics,EnCase]
date: 2021-01-23 16:26:00 +0900
tags: [DigitalForensics,EnCase]
math: true
---
## **EnCase에서 Keyword 검색하기**  

이번 포스팅에서는 EnCase에서 제공해주는 기능 중 하나인 <kbd>Keyword Search</kbd>를 사용하는 방법에 대해 알아보도록 하겠습니다.  


### **1. Keyword Search**

* 이미지 파일에 저장되어 있는 키워드를 찾아야 하는 경우가 종종 있을 것입니다. 예를 들어 용의자의 계좌번호 혹은 메모 같은 것들이 있겠네요. EnCase에서는 **`Processor`**를 통해 키워드 검색을 수행할 수 있습니다. Evidence 홈에서 상단의 **`Process Evidence`**를 선택하고 **`Process`**를 해줍니다.

![upload-image](/assets/post/EnCase/54.png)  

* 프로세서 옵션을 보면 **`Search for keywords`**가 있습니다. 이 항목을 체크해주고 더블클릭해서 값을 지정해주면 됩니다.

![upload-image](/assets/post/EnCase/55.png)  

* 아래 그림과 같이 창이 열리는데 New를 눌러 새 키워드를 생성해주어야 합니다.  

![upload-image](/assets/post/EnCase/56.png)  

* New를 하게 되면 여러가지 옵션을 지정해줄 수 있는데 그냥 Default로 지정해주고 password라는 문자열만 찾아보겠습니다.  

![upload-image](/assets/post/EnCase/57.png)  

* 그리고 하단에 보면 추가로 슬랙 영역을 탐색할 것인지도 설정해줄 수 있습니다. 저는 슬랙 영역까지 탐색을 진행하겠습니다.  

![upload-image](/assets/post/EnCase/58.png)  

* 프로세싱이 끝나면 **`View->Keyword Hits`**에서 키워드 검색 결과를 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/59.png)  

* **`Items`**를 선택하고 **`Unused Disk Area`**를 보면 password값이 있는 것을 알 수 있습니다. **`Compressed View`**를 선택하면 더 보기좋게 키워드 검색 결과를 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/60.png)  


이번 포스팅에서는 키워드 검색을 다뤄봤습니다. 슬랙 영역에 있는 값도 찾아줄 수 있고 검색 결과를 사용자가 보기 편하게 되어 있다는 점이 장점인 것 같습니다.
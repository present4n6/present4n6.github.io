---
title: EnCase(3) - Hash 다루기
comments: true
author: Present4n6
categories: [DigitalForensics,EnCase]
date: 2021-01-19 22:26:00 +0900
tags: [DigitalForensics,EnCase]
math: true
---
## **EnCase에서 Hash 구하기**  

이번 포스팅에서는 EnCase를 활용해서 **`Hash`**와 관련있는 기능을 다뤄보겠습니다. 해시값을 측정하고 이미지 파일에 특정 해시값이 존재하는지 검색해보는 것을 해보겠습니다.  


### **1. 파일 해시값 계산하기(소수 파일 해시값 구하기)**

* 아래 사진을 보면 Image라는 폴더에 여러가지 그림파일들이 있는것을 확인할 수 있습니다. 해당 폴더의 파일들을 대상으로 해시값을 계산하는 방법에 대해 알아보겠습니다.  

![upload-image](/assets/post/EnCase/23.png)  

* 좌측의 **`Tree Pane`**에서 체크박스에 체크를 해주면 해당 폴더의 모든 파일이 선택됩니다. 그리고 **`Table Pane`**에서 우클릭을 하고 **`Entries->Hash/Sig Selected...`**를 선택해줍니다.  

![upload-image](/assets/post/EnCase/24.png)  

* 그러면 아래그림과 같은 창이 뜨는데 해시값을 계산할 수도 있고 파일시그니처를 검증할 수도 있습니다. 저는 해시값 계산만 해보겠습니다.  

![upload-image](/assets/post/EnCase/25.png)  

* 작업이 끝나고 증거 창을 새로고침하면 해시값이 계산되어 있는것을 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/26.png)  


### **2. 파일 해시값 계산하기(모든 파일 해시값 구하기)**

* 이번에는 이미지에 존재하는 모든 파일에 대해 해시값을 계산하는 방법을 해보겠습니다. **`Evidence`**탭의 Home에서 해시값을 구할 이미지 파일을 선택해주고 상단의 **`Process Evidence->Process`** 기능을 선택합니다. 그러면 아래 그림과 같은 창에 새로 열리는데 **`Selected Unprocessed Evidence Files`**를 선택해서 체크한 값에 대해 진행이 되도록 설정한 뒤 아래의 **`Processor Options`**에서 **`Hash analysis`**를 클릭합니다. Options Label에는 그냥 어떤 동작인지 메모해준다고 생각하면 됩니다.   

![upload-image](/assets/post/EnCase/27.png)  

* 그리고 구할 해시값을 선택해주고 OK->OK를 해줍니다.  

![upload-image](/assets/post/EnCase/28.png)  

* Process의 진행사항을 확인하는 방법이 있습니다. 상단의 **`View->Processor Manager`**를 선택해줍니다.  

![upload-image](/assets/post/EnCase/29.png)  

* 그러면 **`Processor Manager`** 탭이 새로 열리는데 아까 입력한 메모도 확인할 수 있고, 프로세스가 얼마나 진행되었는지 퍼센트를 확인할 수 있습니다. 작업중인 프로세스가 여러개일 경우 우클릭하고 우선순위를 지정해줄 수 있습니다.  

![upload-image](/assets/post/EnCase/30.png)  

* 프로세스가 끝나면 이미지 내의 모든 파일에 대한 해시값이 계산된 것을 확인할 수 있습니다.  

![upload-image](/assets/post/EnCase/31.png)  


## **EnCase에서 Hash 검색하기**  

* 앞서 E 볼륨에 Image 폴더가 있는 것을 확인했었습니다. 이번에는 그 폴더에서 특정한 파일이 존재하는지 찾기 위해 HashSet을 만들고 서치하는 방법에 대해 알아보겠습니다. 이러한 기능은 해당 매체에서 어떤 파일이 존재한다는 것을 추정할 수 있고 이를 확인하고자 할 때, 혹은 특정 파일이 존재하는지 서치할 때 유용하게 사용할 수 있습니다.  
저는 저작권이 걸려있는 동물 사진을 유포했다는 접수를 받고 해당 파일들이 실제로 매체 내에 존재하는지 확인해본다고 가정을 하고 진행해보겠습니다.  

### **1. HashLibrary 만들기**

`EnCase Version : EnCase Forensic Training v20.2`  
`Image File OS : Windows 10`

* 우선 유포된것으로 의심되는 파일을 Evidence에 드래그앤드롭으로 올려줍니다.

![upload-image](/assets/post/EnCase/32.png)  

* 그리고 **`Hash Library`**를 하나 생성해줘야 합니다. 해시 라이브러리는 가장 큰 범주라고 보면 될 것 같습니다. 해시가 모여서 해시값이 되고 해시값이 모여서 해시 라이브러리가 된다고 보면 되겠습니다. 상단의 **`Tools->Manage Hash Library...`**를 선택해줍니다.  

![upload-image](/assets/post/EnCase/33.png)  

* **`Manage Hash Library`** 창이 열리는데 **`New`**를 눌러서 새로운 라이브러리를 생성해주도록 합니다. 저는 이 케이스에서만 사용할 것이기 때문에 이 케이스의 경로에 **`Hash Library`**라는 폴더를 생성해주고 지정했습니다. 케이스의 경로는 케이스를 처음 생성할 때 지정을 해줬었습니다. 제 경로는 **`D:\Cases\[CaseName]`** 입니다.  

![upload-image](/assets/post/EnCase/34.png)  

### **2. HashSet 만들기**

* 해시라이브러리를 생성했으면 **`New Hash Set`**을 눌러서 해시셋을 생성해주도록 합니다. 아래 그림과 같이 해시셋의 이름과 태그를 지정해줍니다. 카테고리는 Notable과 None을 지정해줄 수 있는데 Notable로 지정해주겠습니다.(둘의 차이는 기억이 잘 안나네요.)  

![upload-image](/assets/post/EnCase/35.png)  

* 해시셋까지 생성이 완료되면 아래 그림과 같은 결과를 확인할 수 있습니다. **`Count`**는 해시셋에 들어있는 해시값의 수를 의미하는데 아직 들어있는 정보가 없기 때문에 0입니다. 이제 해시셋에 해시를 등록해주는 작업을 해보겠습니다.  

![upload-image](/assets/post/EnCase/36.png)   

* 이제 지금 작업 중인 케이스에 대해 생성한 해시 라이브러리를 적용하기 위해 상단의 **`Case->Hash Libraries...`**를 선택해줍니다.  

![upload-image](/assets/post/EnCase/37.png)  

* **`Primary`**의 경로부분을 클릭해서 아까 생성했던 해시 라이브러리 경로로 지정을 해줍니다. 아래 그림과 같이 보인다면 정상적으로 지정이된 것입니다.  

![upload-image](/assets/post/EnCase/38.png)  

* 앞서 했던것처럼 해당 파일들의 해시값을 구한 뒤, **`우클릭->Entries->Add to hash library...`**를 해줍니다.  

![upload-image](/assets/post/EnCase/39.png)  

* 열린 창에서 해시셋을 선택해주고 OK를 하면 해시셋에 해당 파일의 해시값이 들어가게 됩니다.  

![upload-image](/assets/post/EnCase/40.png)  

* 그리고 상단의 **`Tools->Manage Hash Library...`**에서 다시 확인해보면 파일이 등록되었기 때문에 Count가 5가 된 것을 확인할 수 있습니다. **`Manage Hash Items`**를 통해 등록된 값에 대한 정보도 확인을 할 수 있습니다.  

![upload-image](/assets/post/EnCase/41.png)  

* 해시셋에 값 등록이 끝났으면 구하고자하는 파일 혹은 이미지를 대상으로 해시값을 계산하면 됩니다. 해시값을 계산하게 되면 해시셋에 등록되어 있는 값일 경우 아래 그림처럼 **`Hash Set Names`**탭에 표시가 됩니다. 해당 탭을 더블클릭하게 되면 정렬을 해주기 때문에 모든 파일을 선택하고 **`Hash Set Names`**를 더블클릭해서 해시셋에 등록되어 있는 값과 동일한 파일을 쉽게 찾아볼 수 있습니다.  

![upload-image](/assets/post/EnCase/42.png)  

* 혹은 **`Filter`**기능을 사용해서 결과물을 확인할 수도 있습니다. 하단의 **`Filter Pane`**에서 **`Default->Items->Find Items by Hash Set`**을 선택해줍니다.  

![upload-image](/assets/post/EnCase/43.png)  

* 결과물의 이름을 지정해줍니다.

![upload-image](/assets/post/EnCase/44.png)  

* 찾을 **`HashSet`**의 이름을 지정해줍니다. 위의 **`Invert`**체크박스는 입력값을 제외한 나머지 파일을 찾을 때 지정해주는 옵션입니다.  

![upload-image](/assets/post/EnCase/45.png)  

* 필터를 사용하게 되면 아래 그림처럼 해당하는 파일들만 골라서 보여줍니다.  

![upload-image](/assets/post/EnCase/46.png)  


이번 포스팅에서는 EnCase에서 해시값을 구하는 방법과 또 검색하는 방법에 대해 살펴봤습니다. 해시값을 검색하기 위한 과정이 해야할게 꽤 많은것 같네요. 포렌식학회에서 만든 <kbd>KFOLT</kbd>라는 프로그램이 있습니다. KFOLT가 아직 미완성 프로그램이긴 하지만 해시값같은 것들을 검색하는 방법에 있어서는 조금더 편하다고 느낄 수 있었습니다.  
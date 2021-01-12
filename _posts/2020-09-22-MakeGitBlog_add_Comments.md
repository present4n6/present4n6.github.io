---
title: GitHub 블로그 만들기(3) - disqus 사용해서 댓글 기능 추가하기
comments: true
author: Present4n6
categories: [GitHub, GithubBlog]
date: 2020-09-22 15:49:00 +0900
tags: [GitHub,GitHubBlog]
math: true
---

## **댓글 기능을 추가해볼까?**  

저번 포스팅에서 개발 환경 구축에 대해 다뤄보았습니다. 이번에는 블로그에 댓글 기능을 추가해보도록 하겠습니다.  
**`Jekyll`** 을 사용해서 블로그를 만들게 되면 댓글 기능이 없어서 따로 추가를 해줘야 합니다.  
댓글 기능이 필요 없는 분들도 계시겠지만 저는 방문하는 손님들과 소통을 하는 것이 좋다고 생각해서 추가를 했습니다. 또 댓글을 다는 곳이 없으면 허전하기도 하구요ㅋㅋ    
**`disqus`** 라는 API를 사용해서 추가를 할 건데요, 무료로 댓글 기능을 추가할 수 있어서 많은 사람들이 사용하고 있습니다.  
**`disqus`** 말고 **`utterances`** 도 있습니다. 각자 취향에 맞게 사용하시면 될 것 같습니다.  

* * *
## **댓글 기능 추가 과정**  

### **1. disqus 회원 가입**  

* disqus 홈페이지에 접속해서 회원가입을 진행합니다. [(disqus 홈페이지)](https://disqus.com/)  
페이스북, 구글 등 계정으로 로그인을 할 수 있습니다.  

### **2. disqus 유형 선택**  

* 로그인을 했으면 아래 그림과 같은 화면이 나오는데요, `I want to install Disqus on my site`를 눌러줍니다.  

![upload-image](/assets/post/makegitblog/21.png)  

### **3. Website Name 입력**  

* Website Name을 입력해주시면 됩니다. 여기에 들어가는 값은 추후 **`Shortname`** 이라는 값으로 사용되니 기억해두셔야 합니다.  

![upload-image](/assets/post/makegitblog/22.png)  

### **4. Plan 선택**  

* 그러면 어떤 기능을 사용할지 정하는 창이 나오게 되는데요, 무료로 사용하기 위해서 `Basic`을 선택하시면 됩니다.  

![upload-image](/assets/post/makegitblog/23.png)  

### **5. Platform 선택**  

* 그 다음 어떤 플랫폼을 사용 중인지 고르는 창이 뜹니다. 저는 `Jekyll` 으로 진행하겠습니다.  

![upload-image](/assets/post/makegitblog/24.png)  

### **6. Jekyll 적용 가이드**  

* 그러면 `disqus` 를 Jekyll에 적용하는 방법에 대한 가이드를 해줍니다. **`Universal Embed Code`** 링크를 눌러서 이동해줍니다.  

![upload-image](/assets/post/makegitblog/25.png)  

* 아래로 내리면 아래와 같은 코드를 확인할 수 있는데요 이 코드를 복사해둡니다.  

![upload-image](/assets/post/makegitblog/26.png)  

### **7. Jekyll 소스 코드 수정**  

* 레파지토리 내의 <kbd>_config.yml</kbd>  파일을 열어보면 아래 사진과 같이 **`comments`**에 대한 코드가 있습니다. 이 부분은 `Jekyll` 테마마다 코드가 조금씩 다를 수가 있는데요. `provider` 라고 되어있는 분은 **`disqus`** 를 입력해주시면 됩니다. 저처럼 `boolean` 값으로 설정해야 되는 분들은 **`true`** 로 설정하시면 됩니다.  
그리고 **`shortname`** 값에는 아까 **`Website Name`** 으로 설정했던 값을 넣어주시면 됩니다.  

![upload-image](/assets/post/makegitblog/27.png)  

* 그리고 레파지토리 폴더의 **`_include`** 폴더내에 <kbd>disqus.html</kbd> 라는 파일을 생성해서 방금 복사한 소스 코드를 붙여넣고 저장해줍니다. 저처럼 이미 파일이 존재하는 분들도 계실 수도 있습니다. 그대로 사용해도 되지만 저는 다음과 같이 새로 덮어써줬습니다.  

![upload-image](/assets/post/makegitblog/28.png)  

* 이어서 **`_layout`** 폴더내에 있는 <kbd>post.html</kbd> 파일을 수정해줘야 합니다. 이 파일의 역할은 포스팅되는 페이지의 구조를 담당하고 있는데요, 이 파일에서 아까 생성한 <kbd>disqus.html</kbd> 파일을 호출해줘야 합니다. 이 부분도 테마마다 소스코드가 다를 수 있습니다. `html` 파일 구조를 아시는 분들은 본문에 대한 코드 바로 뒤에 빨간네모로 표시한 소스 코드를 입력하시면 됩니다.  
저는 `chirpy` 테마를 사용중인데 이 테마의 경우 **`conetent`** 뒤에 추가하면 됩니다.  

![upload-image](/assets/post/makegitblog/29.png)  

### **8. 글 작성 시 댓글 기능 포함시키기**

* 다음 과정을 추가적으로 진행해야 댓글 기능이 생성됩니다.  
마크다운 문서를 작성하실 때 아래 사진과 같이 설정을 해줘야 하는데요, `comment=true` 라고 선언을 해줘야 합니다.  
또 다른 방법으로는 **`post.html`** 파일에서 전역으로 선언해주는 방법과 **`_config.yml`** 파일에서 전역으로 설정해주는 방법이 있습니다.  

![upload-image](/assets/post/makegitblog/30.png)  

* 위 과정을 잘 해냈다면 다음과 같이 `disqus` 댓글 창이 생성된 것을 보실 수 있을 것입니다.  

![upload-image](/assets/post/makegitblog/31.png)  

요약해보자면 <kbd>disqus</kbd> API를 불러오는 **`disqus.html`** 파일을 생성하고 포스트를 담당하는 `html` 파일인 **`post.html`** 파일에서 **`disqus.html`** 파일을 호출할 수 있도록 설정해준 것입니다.  
그렇다면 `footer` 를 담당하는 `html` 파일에 코드를 넣어서 모든 페이지에 댓글 기능을 추가하도록 응용해볼 수도 있을 것입니다.  
이 점이 깃 허브 블로그의 장점입니다. 각 파일의 역할에 대해서 알고 있다면 소스코드를 수정해서 본인이 원하는 대로 블로그를 만들어나갈 수 있다는 것입니다.  
다음에는 작성한 파일을 업로드 하기 위해 필요한 설정에 대해 알아보도록 하겠습니다.  
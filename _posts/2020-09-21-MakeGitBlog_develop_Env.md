---
title: GitHub 블로그 만들기(2) - ruby 사용해서 개발환경 구축하기
comments: true
author: Present4n6
categories: [GitHub, GithubBlog]
date: 2020-09-21 16:18:00 +0900
tags: [GitHub,GitHubBlog]
math: true
---

## **개발 환경 구축 왜 해야 하나요?**  

저번 포스팅에서 깃 허브 블로그를 구축했었는데, 깃 허브 블로그는 단점이 하나 있습니다.  
바로 소스코드를 수정하고 commit 하게 되면 실제 블로그에 적용되기까지 딜레이가 존재하는 것입니다.  
실제로 포스팅을 하기 위해서는 어떻게 보이는지 바로바로 확인을 해야 하는 경우가 종종 있는데요,  
일일이 commit 해서 변경 사항을 확인하기보다는 실시간으로 확인하는 방법이 좋겠죠?  
이 문제를 해결하기 위해서 <kbd>bundle exec jekyll serve</kbd> 를 사용해서 실시간으로 블로그의 수정 사항을 확인할 수 있습니다.  
* * *  

## **개발 환경 구축**  
### **1. Ruby 설치**  

* <kbd>bundle exec jekyll serve</kbd> 을 사용하기 위해서는 Ruby를 설치해야 합니다.  
ruby는 [ruby 공식 홈페이지](https://www.ruby-lang.org/ko/documentation/installation/#rubyinstaller) 에서 설치를 할 수 있습니다.  
저는 Windows 환경에서 사용할 것이기 때문에 **`RubyInstaller`** 를 설치했습니다.  
**`RubyInstaller`** 를 클릭해서 이동합니다.  

![upload-image](/assets/post/makegitblog/9.png)  

* 다운로드 버튼을 누르면 됩니다.  

![upload-image](/assets/post/makegitblog/10.png)  

* 굵게 표시 된 파일을 다운로드 받으면 됩니다. 저는 64bit 환경이라 (x64)를 받았습니다.   

![upload-image](/assets/post/makegitblog/11.png)  

* 라이센스에 동의하고 `Next`를 누릅니다.

![upload-image](/assets/post/makegitblog/12.png)  

* 3가지 항목 모두 체크하고 `Next`를 누릅니다.

![upload-image](/assets/post/makegitblog/13.png)  

* 이어서 `Next`를 계속 누르다 보면 `CMD` 창이 열리면서 아래 화면과 같이 뜨는데 <kbd>MSYS2</kbd>
 를 사용하지 않으면 종료하시면 됩니다.  

![upload-image](/assets/post/makegitblog/14.png)  

* 아래 사진처럼 **`ruby -v`**를 입력했을 때 버전이 나오면 정상적으로 진행된 것입니다.  

![upload-image](/assets/post/makegitblog/15.png) 
* * *  

### **2. jekyll bundler 설치**

* 다음 명령어로 <kbd>jekyll bundler</kbd> 을 설치해줍니다.  
```console
$ gem install jekyll bundler
```

* `Git Bash`를 열고 다음과 같이 입력해줍니다.  
```console
$ cd [Repository 폴더 위치]
```  

* **`bundle exec jekyll serve`** 명령어를 입력해주면 다음과 같은 화면을 볼 수 있습니다.  

![upload-image](/assets/post/makegitblog/16.png) 

* 위 화면이 정상적으로 나오면 웹 페이지 주소 창에 **`localhost:4000`** 을 입력해서 블로그의 변경 사항을 실시간으로 확인할 수 있습니다.  
소스코드를 변경하고 저장할 때마다 터미널에서 **`Regenerating`** 이 출력되며, 웹 페이지를 새로고침하면 바로 적용되는 것을 볼 수 있습니다.  
작업이 끝나면 터미널에서 Ctrl+C를 입력해서 종료할 수 있습니다.  

![upload-image](/assets/post/makegitblog/17.png)  

* * *

### **3. bundle exec jekyll serve 오류 해결하기(tzinfo error)**

* **`bundle exec jekyll serve`** 명령어를 입력했는데  
`jekyll 4.1.1 | Error:  tzinfo` 이런 오류가 발생하시는 분들이 계실겁니다.  

![upload-image](/assets/post/makegitblog/18.png)  

* 이런 오류가 뜨시는 분들은 다음과 같이 진행하시면 됩니다.  
레파지토리 폴더 내에 보면 루트 디렉토리에 <kbd>Gemfile</kbd>이라는 파일이 있을 것입니다.  
이 파일을 열고 다음과 같은 내용을 추가해주시면 됩니다.  
```ruby
gem 'tzinfo'
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
```

![upload-image](/assets/post/makegitblog/19.png)  

* 아래와 같은 오류가 뜬다 하시는 분들은 tzinfo를 수동으로 설치해 줘야 합니다.      
```
C:/Ruby26-x64/lib/ruby/gems/2.6.0/gems/bundler-2.1.4/lib/bundler/resolver.rb:290:in `block in verify_gemfile_dependencies_are_found!': Could not find gem 'tzinfo x64-mingw32' in any of the gem sources listed in your Gemfile. (Bundler::GemNotFound)
```

![upload-image](/assets/post/makegitblog/20.png)  

* 레파지토리 폴더의 위치에서 다음 명령어를 입력해서 tzinfo를 설치하면 문제가 해결될 것입니다.  
```console
$ gem install tzinfo -v "~> 1.2"
$ gem install tzinfo-data
```

이번에는 깃 허브 블로그의 개발환경을 만드는 방법에 대해서 다뤄보았습니다. 이렇게 설정을 해두면 일일이 `commit` 해서 확인하는 과정을 거칠 필요 없이 실시간으로 변경 사항을 확인할 수 있습니다.  
다음에는 <kbd>disqus</kbd>를 이용해서 블로그에 댓글 기능을 추가하는 방법에 대해 알아보도록 하겠습니다.
---
layout: post
title: "깃허브 블로그 만들기(설치)"
date: 2018-05-26 23:59:20 +0300
description: Github.io 블로그 설치 및 사용 방법 정리 # Add post description (optional)
img:  # Add image post (optional)
---
## 들어가며
Github를 사용하기 시작하면서 github blog라는 것을 처음 알게 되었고, 또 이런거 알게되면 해봐야 직성이 풀리는 까닭에 시작한 블로그 만들기.
분명 타이틀에서는 15분이면 만든다 했거늘 3시간이 걸려 이제야 쬐금 알게 된 까닭은 무엇일까...ㅠㅠ
암튼 지금부터 정리 시작.

Github 설치 및  기본적인 사용 방법 생략

#### Github Blog 만들기 (Mac OS )
** 사전 설치 사항 **
1. git - 저장소 업로드
2. ruby - jekyll 설치용
3. bundle - ...?? 뭘까..??

###### 1. Jekyll 설치
{% highlight cmd %}
 $ sudo gem install jekyll
{% endhighlight %}
관리자 비밀번호 입력해주면 블라블라 하면서 설치한다. 

###### 2. 블로그 생성 및 local에서 구동해보기
블로그에 대한 자료를 저장할 곳으로 가서 명령어로 만든다.

{% highlight cmd%}
$ jekyll new [git 사용자 이름].github.com //저장공간이 생성된다.
$ cd [git 사용자 이름],github.com
$ jekyll serve // 웹서버 구동
{% endhighlight %}

이렇게 하면 [localhost:4000][localhost]에 웹서버가 올라간다. // $jekyll serve --watch //라고도 쓰던데 백그라운드로 도는 의미인 듯 하지만 잘 안되었음. 문제가 생기면 로그도 뜨니까 걍 --watch 빼고 쓰는게 좋다.

[localhost]: https://localhost:4000

###### 3. github 온라인 저장소 만들기
git을 써서 github에 올리는 것과 똑같다. 대신, repository 이름을 무조건 [github사용자명],github.io로 만들어야 한단다. 이유는 나도 모름.

{% highlight cmd%}
$ git init
$ git remote add origin [저장소 URL]
$ git add .
$ git commirt -m "Comment 달 문구 지정"
$ git push origin master
{% endhighlight %}

이렇게 하면 https://[github사용자명].github.io에 블로그가 생성된다. 아까 local에서 올라간거랑 똑같이 올라간다. 처음 올리면 몇 분 걸린다고 하던데 그냥 파일 올라가는 시간 정도밖에 안드는 듯 하다.

###### 4. Theme 적용
아... 여기서 삽질 개많이 했다.. 그래서 꼭 local에서 구동해보고 가길 권장한다..ㅋ
Theme는 [Jekyll Theme 사이트][jekyllSite]가 있다 여기 들어가서 맘에 드는거 골라서 다운받으면 된다.
아까 만들었던 디렉토리 활용해서 git에 올리면 바로 올라간다.
심지어 그 사람 github 가서 fork로 가져오면 바로 된단다...
근데 난 안됬다.. 꽤오래걸렸다..

어떻게 했냐..

1. 일단 zip으로 다운을 받아서 그대로 아까 jekyll로 만들었던 폴더에 그대로 집어 넣는다.
2. $jekyll serve - 일단 돌려서 local에서 그 사람이 만든 양식대로 돌아가는지 확인한다.
   이 github page의 특성상 그 템플릿을 가져오면 그안에 쓴 글씨, 사진 기타등등 다 받아진다.
   그러기 때문에 화면 혹은 데모에서 본 그대로 동작하는지 실험해본다.
3. 구동이 확인되면 git에 올린다. local에서 구동 잘되면 거의 90프로는 된다.


[jekyllSite]: http://jekyllthemes.org/

###### 삽질 내용
1. 플러그인이라는게 있다고 한다. _config.yml이라는 파일 들어가보면 plugins라는 부분이 있는데 거기에 있는 것들은 따로 설치를 해줘야 된다.
 - 아까 jekyll로 만든 폴더에 _plugins라는 폴더 하나 만들어준다.
 {% highlight cmd%}
 $ sudo gem install [플러그인명]
 {% endhighlight %}
이걸로 플러그인 설치해주면 된다.

자세한 사항들이나 더 궁금한거 있으면 [jekyll 공식 홈페이지][jekyll-ko]같은데 겁나 한글로 잘 번역되어있는 사이트 들어가서 열심히 뒤지면 나온다. 아니면 google검색..ㅎㅎㅎㅎ
댓글에 삽질했던 내용들 공유해주시면 감사하겠습니다.


[jekyll-gh]:  https://jekyllrb-ko.github.io/

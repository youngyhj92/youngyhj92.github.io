---
layout: post
title: Appium Setting
date: 2018-05-28 13:00:00 +0900
description: This is How to setup the github blog page # Add post description (optional)
img: # Add image post (optional)
tags: [Tools, Software, Testing] # add tag
---

##Appium  설치
1. 자바 설치 - 자바 사이트에서
2. Android Sdk 설치 - 보통 안드로이드 스튜디오
3. node.js 설치 - [홈페이지][nodejs]

[nodejs]: https://nodejs.org/en/download/

4. appium client 설치 - [download link][client]

[client]: https://bitbucket.org/appium/appium.app/downloads/.

5. appium-server 설치
	{% highlight command %}
	npm install -g appium
	npm install -g appium-doctor
	{% endhighlight %}
	
	appium-doctor로 확인. - setting 확인 가능
	
	
## Appium Setting
1. dependencies 설치
app.gradle
{% highlight java %}
compile group : 'info.cukes', name:'cucumber-java', version:'1.2.5'
compile group : 'io.appium', name:'java-client', version:'5.0.0-BETA6'
{% endhighlight %}

2. plugins - cucumber for java , Gherkin
안드로이드 스튜디오 혹은 intelliJ에서 플러그인을 설치한다.
cucumber 의 경우 Java와 Kotlin이 두개가 생기면 충돌이 발생한다. 따라서 하나만 설치해 주는 것이 좋다.
(만약 두개가 다 쓰는 경우는 어떻게 하지?에 대한 답은 아직 모르겠다.)

3. 프로그래밍
 - 보통 테스트 프로그램을 제작할 때에는 src/test/java 부분에서 시작한다.
  - Gherkin의 feature 제작과 steps 제작을 위해 하위 디렉토리 밑에 패키지를 만들어 따로 구성한다.
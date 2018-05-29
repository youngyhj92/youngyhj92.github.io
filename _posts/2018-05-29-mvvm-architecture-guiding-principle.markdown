---
layout: post
title: MVVM Architecture Guiding Principle
date: 2018-05-29 13:00:00 +0900
description: This is How to setup the github blog page # Add post description (optional)
img: # Add image post (optional)
tags: [Architecture, Android] # add tag
---

[본문][page]

[page]: https://developer.android.com/jetpack/docs/guide

## mvvm 가이드 원칙

프로그램을 만드는데 있어서 창의적이게 만들어야 하지만 exception이 없어야 한다. 여러 activity들과 Fragment 들과 remote data, persisting locally data 등이 여러 시나리오에서 communicatoin 하는 여러 방법들이 있다. 그렇기에 이 Guide principle은 무조건 따라야 하는 것은 아니지만 경험에 의하여 볼 때, 장기적으로 코드들을 더욱 robust(조직적으로 탄탄한)하고, 테스트가 용이하며, 유지 보수가 잘 이루어질 것이다. 

### 1. Menifest에 정의한 The Entry Point ( Activity, services, broadcast Receivers 둥)은 data Source가 아니다. 
대신 이들은 the subset of data(주제에 직접적으로 연관된 data)로 조직화 해야 한다. 왜냐하면 각각의 App Component들은 사용자와 기기간의 interaction에 의지하고 있는 짧은 생명주기를 가지고 있다. 게다가 개발자들은 그 짧은 생명 주기 동안에만 사용하는 데이터를 원하지 않는다.

### 2. 개발자의 앱에 다양한 모듈간의 책임 범위를 명확하게 정의하여 만들어야 한다.
에를 들어, 네트워크의 데이터를 로드하는 코드들을 여러 클래스 또는 패키지에 중복적으로 삽입하지 말아야 한다.(Boilerplate code)
이와 비슷하게, 연관되지 않는 것들을 억지로 껴넣으려 하지 마라. 에를 들면 data caching(데이터 캐싱 - 데이터 숨기기) , data binding을 같은 클래스에서 만들지 마라.

### 3. 각각의 모듈을 최대한 적게 노출시켜라
하나의 모듈에서 내부 구현 세부 사항을 노출하는 바로가기를 만들지 말아야 한다. 개발자는 짧은 주기에서 짧은 시간을 얻을지 모르지만 코드를 확장하는 과정에서 기술적으로 많은 시간을 소요해야 할 것이다.

### 4. 모듈들간의 상호작용을 정의하는만큼 어떻게 각각의 모듈들을 독립된 상황에서 테스트가 가능하게 만들 것인지 생각해야 한다.
예를들면 네트워크에서 데이터를 fetch(가져오다) 하기 위해 잘 정의된 API를 사용하는 것은 local DB에 있는 data를 유지하는 모듈을 테스트하기 쉽다. 대신에 만약 개발자가 두개의 모듈을 하나의 공간에서 섞는다면, 또는 개발자의 전체 코드 base를 분산시켜 테스르를 하기에 불간할 수 있다.

### 5. 개발자 앱의 핵심은 나머지 부분에서 눈에 띄는 점들이다.
반복적인 코드를 변화시키거나 또는 같은 boilerplate code를 반복적으로 사용하는데 시간을 소비하지 마라. 대신에 개발자의 엠에 유니크한 부분을 만드는데 에너지를 집중하고, 안드로이드 아키텍처 컴포넌트와 boilerplate code를 반복적으로 사용하게 해주는 추천 라이브러리 핸들러를 사용해라.

### 6. 개발자의 앱이 오프라인 모드에서도 사용할 수 있도록 가능한 관련성이 높고 신선한 데이터를 유지해야 한다.
개발자가 지속적이고 빠른 연결성을 즐겨할 때, 사용자는 아닐지도 모른다.

### 7. 개발자의 repository는 하나의 데이터 소스가 하나의 진실된 소스로서 디자인 될 수 있도록 해야 한다.
개발자의 앱이 데이터의 한 부분에 언제든지 접근할 수 있도록 항상 진실된 하나의 소스에서 비롯되어야 한다.
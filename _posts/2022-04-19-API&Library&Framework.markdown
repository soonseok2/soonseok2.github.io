---
layout: post
title: API & Library & Framework
date: 2022-04-19 22:46:26 +0900
category: CS
---

# API ( Application Programming Interface )

> 소프트웨어와의 소통 방법

API 에서 주목해야 할 단어는 Interface 이다.

Inter:face 즉 서로 얼굴을 맞대고 소통을 한다고 생각하면 된다.

이 소통은 사용자와 소프트웨어의 사이에서 이루어진다.

한 문장으로 정리하면 API 는 어떤 소프트웨어에서 제공하는 기능을 제어 및 이용할 때 사용하는 소통방식이다.

보통 Library 와 혼동되는 부분이 많은데, API 가 추상적인 개념이라는 것은 어느정도 이해가 되지만,

정확히 어떤 요소가 API와 Library 를 구분짓느냐고 묻는다면, 생각이 조금 복잡해진다.

Java API 를 예시로 들어보자, 우리는 System 이나 String 등의 클래스를 사용하고 싶다.

이 때 해당 기능들이 적당히 묶인 것을 Library 라고 하면, 사용자는 API라는 방법을 통해서 해당 Library 를 사용하게 되는 것이다.

주로 혼동되는 이유는 API 와 Library 가 함께 제공되는 경우가 많아서인듯 하다.

<br/>

# Library

> 코드 뭉치들이 꽂혀있는 도서관

Library 는 말 그대로 도서관이라고 볼 수 있다.

이 도서관에 꽂혀있는 책들은, 어떤 공통된 목적이나 주제를 가지는 기능(함수) 들이다.

즉 Library 는 한 문장으로 정리하면, 공통된 목적이나 주제를 가지는 기능들의 집합이라고 볼 수 있다.

Library 스스로는 Application 을 만들지 못하지만, 사용자가 능동적으로 가져가서 사용할 수 있다.

마치 도서관에서 책을 빌려서 읽듯이, 개발중인 Application 에서 Library 를 빌려서 사용한다고 생각할 수 있다.

API 가 추상적인 개념이었던것에 비하여, Library 는 실제 실존하는 기능(코드 뭉치)를 뜻한다.

허나 위에서 말했듯이 API 와 Library 가 보통 함께 제공되는 경우가 많으므로, 큰 맥락에서는 혼용해서 단어를 사용할 때도 있는듯 하다.

<br/>

# Framework

> 소프트웨어의 설계 기틀

Framework 는 위의 API 나 Library 보다 좀 더 나아가서 큰 그림을 그린다.

단지 class 와 method 들을 제공할 뿐만 아니라, 어떤 구조로 Application 을 만들어야 할지 제공한다.

API 와 구분이 명확하지는 않아서 종종 혼동 될 수도 있다.

차이점을 적어보자면, API 는 내가 생각하는 프로그램의 흐름대로 필요한 곳에서 호출하여 능동적으로 사용한다.

하지만 Framework 는 Spring framework 를 예시로 들면, Spring framework 의 흐름을 따라서 Application 을 작성해야 한다.

또 제어의 역전이 일어나서 수동적으로 사용하기도 한다.

전반적으로 Framework 의 경우에는 API 에 비하여 내 Application 에 끼치는 영향이 상대적으로 더 크다.

Framework 는 보통 API, Library 들의 집합으로 제공되며, 사용자가 이용할 수 있는 부분이 한정되기도 한다.

<br/>
# Summary

요약하자면, API 는 Application 과의 소통 방법, Library 는 기능을 가진 코드 뭉치들, Framework 는 Application 설계용 틀이라고 볼 수 있다. 사용자는 API 를 통해 Library 들을 사용하며 Framework 뼈대에 살과 근육을 붙이면서 특정 Application 을 만들어낸다.

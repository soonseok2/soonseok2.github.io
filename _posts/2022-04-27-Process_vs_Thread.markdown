---
layout: post
title: Process vs. Thread
date: 2022-04-27 12:00:00 +0900
category: CS
---

# Intro

Process 와 Thread 는 언어의 혼용때문에 헷갈리는 개념 중 하나이다.
각자의 특징을 확실하게 구분지어서 차이점을 알아보자.
밑에서 설명할 내용들은 우선 단일 CPU Core 기준이라고 가정하자.

# Process

> 실행중인 프로그램

우리가 실제로 구현하는 코드 뭉치들은 프로그램이라고 불린다.
Process 는 프로그램이라는 코드 뭉치들이 실행중인 상태를 말한다.
다르게 얘기하자면 OS 로부터 시스템 자원을 할당 받는 작업의 단위라고도 할 수 있다.
Code, Data, Heap, Stack 네 가지 영역으로 이루어진 메모리 공간을 확보하게 된다. (동시에 PCB 도 생성된다.)
Process 자체적으로 작업하지는 않고, 하위 Thread 를 사용하여 작업을 진행한다.
즉 Process 단위로 작업하는 것처럼 보이는 것은, 사실 해당 Process 내의 단일 Thread 가 작업하고 있는것이다.

# Thread

> Process 내의 작업자

Thread 는 한 Process 내에서 구분지어진 실행 단위이다.
우리가 실제로 프로그램을 실행하면 Thread 단위로 실행되는 것이다.
Process 의 Code, Data, Heap 메모리를 공유하여 사용하며, 자체적으로는 Stack 메모리 공간만 확보한다.

# Concurrency

> 그럴듯한 눈속임

유저들은 컴퓨터를 사용할 때 보통 여러가지 프로그램들을 동시에 실행한다.
하지만 컴퓨터의 CPU ( 내부의 Core ) 는 동시에 한가지 Process 만 실행이 가능하다.
이를 동시성이라고 부르는데, 실제로 CPU 는 동시에 여러 작업을 실행하는 것이 아니고,
빠른 속도로 여러 작업을 옮겨다님으로써 동시에 실행하는 것처럼 보이게 한다. ( CPU 시간을 분할한다고 표현한다. )
이 때 작업 사이를 옮겨다니는 행위를 Context switching 이라고 부르고, 내부적으로는 메모리 공간을 계속 바꿔서 참조한다.

# Multi-process vs. Multi-thread

> 개인주의와 연대책임

개념을 헷갈리지 않기 위해, 한 어플리케이션이 여러 동작을 수행하는 웹 브라우저 ( Chrome, Internet Explorer ) 의 예를 들어보자.
<br/><br/>
Chrome 은 Multi-process 의 예시를 보여주는데, Chrome 의 각 탭들은 사실은 각각 하나의 Process 이다.
Chrome 은 fork() 를 통해 Child Process 를 만들어내고, 모두 각자의 Code, Data, Heap, Stack 메모리 공간을 확보하게 된다.
어떤 탭은 노래를 틀고, 어떤 탭은 인터넷을 보는 등의 행위를 할텐데, 이 때 계속해서 Context switching 이 일어나게 된다.
이렇게 메모리 공간이 분리되어 있기 때문에, 각 Process 들은 독립적이고, Context switching 비용은 꽤나 클 것이다.
또 Process 들이 서로의 정보가 필요할 때는 Inter Process Communication 으로 통신해야 한다.
Chrome 은 한 탭이 응답불가 상태가 되어도, 다른 탭은 멀쩡하게 동작하는 것을 알 수 있다.
<br/><br/>
반면에 IE 는 Multi-thread 방식을 사용하고 있다. IE 의 여러 탭들은 Thread 들이다.
각 Thread 들은 자신이 속한 process 의 Code, Data, Heap 영역을 공유하며, 오직 Stack 공간만 가진다고 하였다.
따라서 완전히 독립적이지 않고, Context switching 비용은 상대적으로 적을 것이다.
Thread 사이에 공유하는 메모리 공간이 존재하기 때문에, IPC 보다 편하게 통신할 수 있다.
하지만, IE 는 Process 가 응답 불가 상태가 된다면, 모든 Thread 가 같이 죽어버린다는 것을 알 수 있다.
즉 공유하는 자원을 관리해야하며, 각 Thread 간의 충돌을 주의하여야 한다.

# Multi-core

> 눈속임이 아니다

Multi-core 는 말 그대로 Core 가 물리적으로 여러개 존재하는 것으로, 물리적 병렬 작업을 지원한다.
동시성은 하나의 Core 에서 하나 이상의 Process 나 Thread 가 동시에 작업하는 눈속임이라고 했었다.
Multi-core 는 둘 이상의 Core 에서 한꺼번에 하나 이상의 Process 나 Thread 가 실제로 동시에 작업하는 것을 의미한다.
하지만, 눈속임이 아닌 실제로 병렬 작업을 위해서는 Core 간의 통신, 충돌 관리 등을 고려해야 할 것이다.


<br/>
# Summary

Process 는 독립적으로 메모리 공간을 가지며, 서로 통신을 위해 IPC 가 필요하고, Context switching 비용이 크다.
Thread 는 공유 메모리를 가지며, Context switching 비용이 적지만, 충돌 관리를 해야 한다.
Concurrency 는 CPU 시분할로 동시에 실행하는 것 처럼 보이는 눈속임이다.
Multi-core 는 물리적으로 여러개의 Core 가 병렬적으로 작업하는 것이다.
---
title:  "컨테이너 기술의 발전"
excerpt: "도커 컨테이너 기술의 발전 "
toc: true
toc_sticky: true
categories:
  - Linux
tags:
  - linux
  - os
  - docker
last_modified_at: 2023-06-20T08:06:00-05:00
---



개발을 하다보면 한번쯤 도커에 대해서 들어본 적이 있을 것입니다. Docker.   

뭔지 잘 모르겠지만 어려운 느낌이 물씬 풍기는 단어 입니다. 한 번 들은 것도 아니고 수없이 많이 들은 도커에 대해서 유창하지는 않더라도 어떤 개념인지 간단하게라도 찍먹은 해봐야 하지 않을까 싶은 생각에 도커 공부를 시작하기로 마음 먹었습니다. 불끈!  

오늘은 간단하게 도커가 탄생하게 된 배경, 기술의 발전을 살펴보면서 도커에 대해서 감을 잡아가는 시간을 갖도록 하겠습니다.   
  

기업들이 시스템을 개발하고 서비스를 운영함에 있어서 직면하는 문제점 중 하나는 다음과 같습니다. 

> 어떻게 서비스를 효율적으로 운영할 것인가?
> 


![tux-158547_640.webp](/assets/images/posts/2023/tux-158547_640.webp)

# 1. 전통적인 서비스 운영

컴퓨터 하드웨어에 운영체계를 설치하고, 그 위에 라이브러리와 프레임워크를 설치한 후에 어플리케이션을 개발하는 방식을 말합니다. 

그 자체 어플리케이션 만으로 보면 문제 없어 보이는 시스템에 다른 어플리케이션이 추가되어 개발이 진행되면서 몇 가지 문제점을 맞이하게 됩니다. 

- 비용 효율성
- 컴퓨팅 자원을 최대한 활용하는 방법

하나의 환경에서 여러 어플리케이션이 동작하면서 공통된 라이브러리를 사용하는 경우, 그러나 버전은 다를 경우 충돌이 발생할 수 있습니다. 이러한 충돌을 막기 위해서 각각의 어플리케이션을 서로 격리 하는 기능이 필요한데요. 그렇게 발전된 기술이 **가상화** 입니다. 

# 2. 가상 환경 운영

가상화 시스템은 컴퓨터 하드웨어 위에 운영체제를 설치하는 것까지는 똑같으나 그 위에 Hypervisor 라는 가상머신을 관리하는 컴포넌트가 올라가게 됩니다. 

## 장점

가상머신에는 각각의 Guest OS가 동작하게 되고, CPU, RAM, 파일시스템과 같은 자원을 각각 할당받게 되니 어플리케이션 입장에서는 다른 어플리케이션과 격리된 공간을 할당 받고 전통적인 방식에서 언급한 충돌 문제가 없게 되는 것입니다. 

## 단점

그러나 단점도 물론 존재합니다. 가상머신 이라고는 하지만 어쨋든 물리적으로 제한된 컴퓨팅 하드웨어 기반으로 동작하는 것을 여러 가상머신으로 나눈 것이라 성능의 효율성이 떨어진다는 것입니다. 

또한 Guest OS를 에뮬레이팅 하기 위해 CPU와 RAM이 필요하게 되는데 각각의 어플리케이션을 동작시키기 위해서 기본적으로 필요한 자원이 공통적으로 필요하다 보니 자원의 오버헤드가 증가한다는 점입니다. 

이러한 문제점이 있다 보니 어떻게 하면 가상머신을 좀더 경량화 하고 성능을 끌어올릴 수 있을까 하는 고민이 이어졌습니다. 그래서 나온 기술이 바로 **도커** 입니다. 


![space-19070_640.jpg](/assets/images/posts/2023/space-19070_640.jpg)

# 3. 컨테이너 운영

도커는 컨테이너 엔진 중에 하나인데요. 많이 들어본 도커는 유일한 컨테이너 기술도 아니고, 가장 처음 만들어진 컨테이너 기술도 아닙니다. 그러나 가장 널리 쓰이는 컨테이너 엔진으로 도커를 뽑을 수 있습니다. 

컨테이너는 여러가지 격리 기술을 사용한 프로세스 라고 보시면 됩니다.  Linux의 namespace 기술과 chroot 기술을 활용하게 됩니다. 

## 장점

Guest OS 위에서 동작하는 것이 아니고 Host OS 상에서 동작하다 보니 성능이 떨어지지도 않으며, CPU와 같은 여러 자원들을 에뮬레이팅 할 필요도 없어 자원 오버헤드도 줄어들게 됩니다. 

# 4. Kubernetes 운영

그렇다면 쿠버네티스란 무엇일까요? 쿠버네티스는 컨테이너 오케스트레이션 시스템 입니다. 도커와 마찬가지로 유일한 오케스트레이션 시스템도 아니고, 처음 나온 시스템도 아니지만 거의 표준이 되어 가고 있는 컨테이너 오케스트레이션 시스템 이라고 할 수 있습니다. 

오케스트레이션 이라는 단어에서 알 수 있듯이 클러스터 환경에서 컨테이너를 보다 효율적이게 관리하는 용도로 사용됩니다. 

도커가 전통적인 시스템의 어떤 단점을 극복하기 위해서 만들어진 시스템인지 찍먹 해봤습니다. 도커의 바다에서 길을 잃지 않기 위해 차근차근 공부해보도록 하겠습니다.
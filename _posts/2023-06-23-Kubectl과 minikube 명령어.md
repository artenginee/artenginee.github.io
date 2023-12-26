---
title:  "Kubectl 과 minikube 명령어"
excerpt: "Kubectl과 Kustomize, 그리고 minikube 명령어에 대하여"
toc: true
toc_sticky: true
categories:
  - Linux
tags:
  - linux
  - os
  - docker
last_modified_at: 2023-06-23T08:06:00-05:00
---


# Kubectl 과 minikube 명령어

지난 포스팅에서 Docker와 Kubenetes에 대해서 간략?하게 알아보았는데요. 오늘은 쿠버네티스 환경을 구축하는데 필요한 도구들과 간단한 명령어들에 대해서 알아보도록 하겠습니다. 
<br><br>


# kubectl

쿠버네티스 환경을 보면 클러스터 시스템으로 이루어져 있습니다. 클러스터 시스템에는 Master node가 있고, 주변에 worker node가 있는데요. Master node가 주변의 Worker node를 관리하는 구조입니다. 

kubectl은 쿠버네티스의 API 서버와 통신하여 사용자 명령을 전달할 수 있는 CLI 도구 입니다. 
<br><br>

# kustomize

kustomize는 쿠버네티스의 메니페스트 파일을 좀 더 효율적으로 관리할 수 있도록 도와주는 도구 입니다. kubectl을 관리하는 용도로 사용되는 대표적인 프로그램은 크게 두 가지가 있습니다. kustomize 와 Helm 입니다. 아직 쿠린이 입장에서는 Helm을 더 많이 들어봤는데요. kustomize는 kubectl과 같이 설치되며 쿠버네티스 환경에서 만들어진 프로그램 입니다. 반면에 Helm은 오픈소스로 kubectl을 관리하는데 많이 사용합니다.
  
    
      
  
  
  
<br><br>

# minikube

쿠버네티스 환경을 구축하려면 클러스터 환경을 구축해야 합니다. 여러 컴퓨터에 분산되어 있어야 하며, 서로 유기적으로 통신이 가능토록 설정되어 있어야 하죠. 처음 쿠버네티스를 배우려는 쿠린이 입장에서는 그런 환경을 구축하고 실습을 하기가 어렵습니다. 그래서 나온 것이 이름에서도 알 수 있는 작고 소중한 minikube 입니다. 

minikube는 가상환경을 사용하여 쿠버네티스 클러스터를 구현합니다. 드라이버를 선택하여 원하는 가상환경 (docker, podman, virtualbox, parallel, vmware, hyperkit 등)에서 구성 가능합니다. 

## minikube 기본 사용법

- 쿠버네티스 클러스터 상태 확인

```bash
$ minikube status
```

- 쿠버네티스 클러스터 중지

```bash
$ minikube stop
```

- 쿠버네티스 클러스터 삭제

```bash
$ minikube delete
```

- 쿠버네티스 클러스터 일시 중지

```bash
$ minikube pause
```

- 쿠버네티스 클러스터 재개

```bash
$ minikube unpause
```

- minikube 애드온 목록 화인

```bash
$ minikube addons list
```

쿠버네티스 클러스터 필요한 애드온들을 설치해서 운영하게 되는데요. minikube는 몇 가지 애드온들에 대해서 손쉽게 설치할 수 있는 방법을 제공합니다. 

- minikube 애드온 활성화

```bash
$ minikube addons enable [addon]
```

앞에서 설명한 `minikube addons list` 명령어로 목록을 확인한 후 설치하고자 하는 애드온을 활성화 시킬 수 있습니다. 

- minikube 애드온 비활성화

```bash
$ minikube addons disable [addon]
```

- 쿠버네티스 클러스터 노드에 SSH 접속

```bash
$ minikube ssh
```

- 쿠버네티스 클러스터 버전과 대응되는 kubectl 사용

```bash
$ minikube kubectl ... 
```
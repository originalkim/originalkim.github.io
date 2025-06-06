---
title: 프로토콜과 네트워크 참조 모델
description: "프로토콜(Protocol)과 네트워크 참조 모델(Reference Model)에 대해 알아보자."
fa_icon: fa-solid fa-network-wired
author: yulmwu
date: 2025-05-08 00:00:00 +0900
categories: ["A. 개념/용어 정리", "네트워크"]
tags: ["네트워크", "프로토콜", "참조 모델"]
use_math: true
previous_post: 
    title: "메세지 교환 방식과 유니캐스트, 브로드캐스트"
    path: "3-message-switching"
next_post: 
    title: "OSI 7계층과 TCP/IP 4계층, 캡슐화/역캡슐화"
    path: "5-osi7layer-tcpip4layer"
series: 
    title: "네트워크 개념 정리"
    color: "bg-notion-pink"
    ep: 4
    ep_color: "bg-notion-purple"
order: 2004
---

## 프로토콜(Protocol)

쉽게 말해 통신 과정에서 **올바르게 데이터(메세지)를 전달하기 위해선 어떠한 정해진 규약, 규칙이 필요함.**

전에 설명한 패킷은 택배와 상당히 비슷한데, 택배엔 택배를 받는 수신지(수신지 호스트의 정보)와 보낸 사람(송신지의 정보) 이들이 담긴 송장(헤더)와 내용물인 페이로드가 있다고 생각하면 됨.

그럼 택배를 보낼 땐

1. 보낼 물건(페이로드)를 택배(패킷) 상자에 담음.
2. 배송 주소(송신/수신지)를 적고 부가적인 정보 등을 택배의 송장에 기입함.
3. 택배 업체(기사) (네트워크 장비)를 통해 발송함.

그런데 보낸 사람이던, 받는 사람이던, 택배 업체의 기사님이던 올바르게 전달이 되려면 송장 등에 담긴 정보를 올바르게 해석할 수 있게 규약이 있어야겠지?

⇒ 이게 **프로토콜**임.

즉 **프로토콜**은 노드가 주고받는 정보를 올바르게 전달하기 위한 규칙이나 규약, 또는 방법을 의미함.

대표적으로 IP 주소를 사용하여 패킷을 수신지까지 전달하는 IP(Internet Protocol), MAC 주소와 IP 주소를 변환해주는 ARP 프로토콜,  웹 상에서 주로 사용되는 HTTP/HTTPS, 그리고 TCP, UDP 등도 모두 프로토콜임.

이러한 **프로토콜은 저마다 각각의 특성과 목적이 있다는 점**, 그러한 목적에 따라 프로토콜을 통해 정해진 규약으로 정보가 전달되고 처리된다는게 핵심임.

## 네트워크 참조 모델

프로토콜은 택배의 규격, 송장의 규약 등을 정의한다고 했을 때, 네트워크 참조 모델은 패킷이 처리되는 순서 등의 모델을 정의해둔것이 **네트워크 참조 모델(Network Reference Model)**임.

아까 택배 예시에서 발송하고 전달받는 순서를 보면

1. 보낼 물건(페이로드)를 택배 상자(패킷)에 담음
2. 테이프 등을 사용하여 택배를 포장함
3. 업체(편의점 택배, 우체국 등)에 택배를 발송함

이 됨. 하지만 반대편(받는) 입장에서 보면?

1. 업체의 기사님을 통해 택배를 전달받음
2. 테이프를 제거하여 택배를 개봉함
3. 보낸 물건을 확인함

이렇게 보낼때의 과정과 받을때의 과정이 거의 비슷한데, 네트워크에서도 마찬가지임.

그리고 이렇게 네트워크에서 통신의 과정을 **계층별로** 나눈게? ⇒ **네트워크 참조 모델**임.

#### 굳이 왜 쓰는가?

먼저 네트워크를 구성하고 설계할 때, 참조 모델을 참조하면 쉽고 빠르게, 효율적으로 설계하거나 구성할 수 있음.

다만 모든 네트워크의 흐름과 구조가 네트워크 참조 모델을 따라가는게 아니고, 꼭 지켜야하는 것 도 아니지만 따르는게 좋다고 생각함.

추가로 참조 모델을 사용하여 구성했다는건, 오류나 문제가 발생했을 때 그 문제의 원인을 찾기도 쉽다는 의미가 됨.

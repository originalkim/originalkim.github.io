---
title: "인터넷을 구현하는 네트워크 계층"
description: "네트워크 계층의 역할과 기능에 대해 알아보자."
fa_icon: fa-solid fa-network-wired
author: yulmwu
date: 2025-05-08 00:00:00 +0900
categories: ["A. 개념/용어 정리", "네트워크"]
tags: ["네트워크", "네트워크 계층", "OSI 7계층"]
use_math: true
previous_post: 
    title: "네트워크 장비: 허브, 스위치"
    path: "hub-switch"
series: 
    title: "네트워크 개념 정리"
    color: "bg-notion-pink"
    ep: 8
    ep_color: "bg-notion-purple"
order: 2008
---

## 인터넷을 구현하는 네트워크 계층

여태 까지의 계층은 물리 계층~데이터링크 계층으로, 주로 LAN의 범위에서 다뤘음.

그런데 이러한 LAN은 그의 범위가 좁아 지구 반대편의 컴퓨터와 통신하기엔 어려운데, 그렇게 인터넷을 가능케 하는 계층이 네트워크 계층임.

네트워크 계층에선 IP(Internet Protocol)라는 프로토콜을 사용하며, 라우터(Router)라는 장비를 통해 최적의 경로로 라우팅(Routing)하여 경로를 설정하고 인터넷을 구현함.

### IP(Internet Protocol)

먼저 MAC 주소를 다시 생각해보자. NIC(Network Interface Card)에 박혀있는 고유한 주소라고 하였는데, 이를 사용하여 송신지를 정할 순 있음.

하지만 송신지 호스트의 MAC 주소를 모른다면? ⇒ 당연히 못찾아감.

그래서 네트워크 계층에선 MAC 주소와 함께 IP 주소를 같이 쓰는데, 이러한 IP는 호스트마다 부여됨.

MAC 주소와는 다르게 변경이 가능하며, 직접 할당하거나 DHCP(Dynamic Host Config.. Protocol)라는 프로토콜을 통해 자동으로 할당할 수 도 있음.

(때문에 IP는 논리 주소라고도 불림)

이러한 IP 주소는 ARP(Address Resolution Protocol, 주소 결정 프로토콜)라는 프로토클을 사용하여 MAC 주소로 변환되어 네트워크 상에서 경로를 찾게됨.

네트워크 계층의 가장 핵심적인 프로토콜인데, 두가지 버전이 있음. 하나는 IPv4(기본)이고 다른 하나는 IPv6임.

#### IPv4 (버전 4)

4바이트, 즉 32비트 크기의 주소임. 1바이트(8비트, 0~255)의 옥텟(octet)을 닷(`.`)으로 구분함.

즉 192.123.123.123 같은 주소는 IPv4 주소라는거. TODO…

#### IPv6 (버전 6)

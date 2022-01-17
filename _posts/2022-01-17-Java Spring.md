---
layout: post
title:  "Java Spring"
summary: "Study / Java Spring"
author: lymchgmk
date: '2022-01-17 22:28:00 +0900'
category: Study
thumbnail: /assets/img/posts/Spring_logo.svg
keywords: post
permalink: /blog/study-java-spring
usemathjax: false
comments: true
---

# Java Spring

## 1. 개요

> Dependency injection, Transaction management가 핵심 기능인 framework

- `Java SE` + 기존 `Java EE(Enterprise edition)`를 사용해서 DI, DB, transaction 처리하던 것을 `Java SE` + `Spring`으로 바뀜.	
  - 유료화, 불편했기 때문



- MVC(model 2) <- DI <- 느슨한 결합력과 인터페이스
- Tranction <- AOP
- 인증과 권한 <- Servlet Filter



## 2. 느슨한 결합력와 인터페이스

> 어떤 객체를 효율적으로 수정하기 위한 구조는 어떤 것일까?


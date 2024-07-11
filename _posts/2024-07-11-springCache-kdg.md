---
title: "Spring Cache"
date: 2024-07-11 00:00:00 -0000
categories: wiki
author: kdg1986
tags: wiki spring cache
---

# Caching

캐싱은 데이터나 계산 결과를 임시로 저장하는 기술 또는 메커니즘을 가리킵니다.

클라이언트에 요청에 따라 데이터에 접근할 떄 발생하는 비용을 줄이고 성능향상을 목적으로 사용합니다.

## Cache Hit

참조 하려는 데이터가 캐시에 존재할 때를 말합니다.

## Cache Miss

참조 하려는 데이터가 캐시에 존재하지 않을 때를 말합니다.

## Cache Hit Ratio (캐시 히트율)

(cache hit 횟수)/(전체참조횟수) = (cache hit 횟수)/(cache hit 횟수 + cache miss 횟수)

캐시 활용도를 높이기 위해서는 캐시 히트율을 올리는 것이 중요합니다.

캐시 히트율을 높이려면 자주 참조되며 수정이 잘 발생하지 않는 데이터들로 구성해야 합니다.


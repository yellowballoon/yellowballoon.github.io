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

## Local Cache

로컬 서버 내부 저장소에 데이터를 캐시합니다.

해당 서버에 데이터가 있어서 속도가 빠르다는 장점이 있지만

다중 서버 환경에서는 각 서버에 중복된 데이터를 캐싱해야하고 서버간 데이터 일관성이 깨질 수 있습니다.

## Global Cache

별도의 저장소에 데이터를 캐싱 하는 것입니다.

저장소에 접근하는 부분이 있어 로컬에 비해 속도가 느리지만 중복데이터나 일관성에 문제가 없다는 장점이 있습니다.

# Spring Cache

스프링 캐시 추상화는 여러 캐시 프로바이더를 의존합니다.

- Generic
- JCache (JSR-107) (EhCache 3, Hazelcast, Infinispan, and others)
- Hazelcast
- Infinispan
- Couchbase
- Redis
- Caffeine
- Cache2k
- Simple

# Annotation

https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/cache/annotation/package-summary.html


## @Cacheable

클래스/메소드에 사용이 가능함.

여러 속성값을 통해 캐시 상태를 관리 하고 저장 할 수 있음.

속성값에 조건을 입력하여 특정 조건일때만 캐시하도록 처리도 가능함.

조건에 부합하는 캐시가 있는경우 캐시를에 저장된 데이터를 서빙함.

```java

    @RequestMapping("/api/test")
    @Cacheable(cacheNames = "my",key = "#root.methodName")    
    List<UserDTO> test(HttpServletRequest req) {
        return userService.getTestUser();
    }

```
- 캐시이름 : my
- key : test 에 캐시를 저장함
- #root 는 예약어 ( methodName , target , args , caches )

## @CachePut

클래스/메소드에 사용이 가능함.

캐시를 단순 저장하는 용도로만 사용하는 어노테이션


```java

    @RequestMapping("/api/test")
    @CachePut(cacheNames = "my",key = "#root.methodName")    
    List<UserDTO> test(HttpServletRequest req) {
        return userService.getTestUser();
    }

```
- 캐시이름 : my
- key : test 에 캐시를 저장함
- #root 는 예약어 ( methodName , target , args , caches )


## @CacheEvict

클래스/메소드에 사용이 가능함.

캐시를 삭제하는 어노테이션

```java

    @RequestMapping("/api/test/{code}")
    @Cacheable(key = "#code",value = "my")
    @CacheEvict(key = "#code",value = "my",condition = "#code == '2'" , beforeInvocation = true)
    List<UserDTO> test(@PathVariable String code ) {
        return userService.getTestUser();
    }

```
- 캐시이름 : my ( value는 cacheNames의 alias임 )
- key : code 파라미터 값
- condition : code값이 2인경우에만 트리거 됨.
- beforeInvocation : 메소드를 실행하기 전에 캐시를 삭제 처리함.
---
title: "Spring Cache"
date: 2024-08-21 00:00:00 -0000
categories: wiki
author: bokyung
tags: wiki spring cache
---

## Caching

![Alt text](https://velog.velcdn.com/images%2Fqotndus43%2Fpost%2Fc7bca826-b0a6-46dc-a1a3-596e4c391cec%2Fimage.png)
![Alt text](https://velog.velcdn.com/images%2Fqotndus43%2Fpost%2Ffeff5526-f6f8-4290-8c30-4dcfc28b7033%2Fimage.png)

- cache hit : 참조하려는 데이터가 캐시에 존재할 때 cache hit라 합니다.
- cache miss : 참조하려는 데이터가 캐시에 존재 하지 않을 때 cache miss라 합니다.

## Caching 이란?

- 캐싱는 메모리에 데이터를 미리 적재하고 이를 빠르게 읽어 응답하는 구조입니다.

- 캐시는 서버의 부담을 줄이고, 성능을 높이기 위해 사용되는 기술입니다. 예를 들어 어떤 요청을 처리하는데 계산이 복잡하거나 혹은 DB에서 조회하는게 오래 걸리는 등에 적용하여 결과를 저장해두고 가져옴으로써 빠르게 처리할 수 있습니다.
캐시는 값을 저장해두고 불러오기 때문에 반복적으로 동일한 결과를 반환하는 경우에 용이합니다. 만약 매번 다른 결과를 돌려줘야 하는 상황에 캐시를 적용한다면 오히려 성능이 떨어지게 됩니다. 오히려 캐시에 저장하거나 캐시를 확인하는 작업 때문에 부하가 생기기 때문입니다. 그러므로 캐시는 동일한 결과를 반환하는 반복적인 작업과 시간이 오래 걸려서 서버(애플리케이션)에 부담이 되는 경우에 적용하면 좋습니다

## Spring Cache

- 스프링은 AOP 방식으로 편리하게 메소드에 캐시 서비스를 적용하는 기능을 제공하고 있습니다.

- 일부 데이터를 미리 메모리 저장소에 저장하고 저장된 데이터를 다시 읽어 사용하는 캐시 기능을 제공하고 있습니다.

- @Cacheable : 캐시 생성 및 전달을 담당합니다. 캐시에 데이터가 없을 경우에는 기존의 로직을 실행 후 캐시에 데이터를 추가하고, 캐시에 데이터가 있으면 캐시의 데이터를 반환합니다.

- @CachePut : 캐시 내용 수정을 담당합니다. @Cacheable과 유사하게 실행 결과를 캐시에 저장하지만, 조회시에 저장된 캐시 내용을 사용하지 않고 메서드를 실행합니다.

- @CacheEvict : 캐식 삭제를 담당합니다. 캐시 이름을 넣어주면 메소드가 실행될 때 캐시의 내용이 제거됩니다.

### 장점 
 - 성능 향상 : 캐시를 활용하여 데이터 접근 시간을 단축할 수 있어 애플리케이션 성능이 향상됩니다.

 - 코드 간결성 : 스프링 캐시 추상화를 사용하여 캐시를 쉽게 적용할 수 있습니다.

 - 유연성 : 다양한 캐시 구현체와 쉽게 연동할 수 있습니다.

 ### 단점
 - 메모리 사용 증가 : 캐시는 메모리를 사용하므로, 잘못된 설정으로 메모리 부족 문제가 발생할 수 있습니다.

 - 복잡성 증가 : 캐시 전략, 무효화 타이밍 등을 적절하게 설정하지 않으면 데이터 일관성 문제가 생길 수 있습니다.
---
layout: post
title: "CH2 Creating and Destroying Objects"
comment: true
categories:
  - programming
  - JAVA
tags:
  - Effective JAVA 3rd
---

object 만들고 없애는 것을 다룬다.

### 1. 생성자 대신 static factory method 고려하기.

Boolean으로 예시를 들어보자면 아래와 같다!
<br />
<code>
public static Boolean valueOf(boolean b) {
	return b ? Boolean.TRUE : Boolean.FALSE;
}
</code>
<br />
클래스가 클라이언트에게 static factory method를 생성자 대신 또는 같이 제공 할 수 있다. 

<hr/>

#### 장점

1. 이름이 있다!  메소드가 이해하기 쉬움
  * BigInteger(int, int, Random)    < BigInteger.probablePrime

2. 새 오브젝트를 만들 필요 없다.
  * immutable 클래스의 경우 이미 생성된 인스턴스를 다시 사용할 수 있다
  * 불필요하게 중복된 인스턴스들이 생성되는 것을 방지하기 위해 이미 생성된 인스턴스를 저장했다가 반복 사용 가능.

  * Flyweight 패턴과 유사
  * : 객체 생성시 자원/시간이 많이 들면 프로그램 성능 크게 향상시킬 수 있다

  * : 여러번 호출되어도 이미 생성된 동일 객체를 반환하기 때문에 클래스에서 언제든지 인스턴스 존재를 직접 제어할 수 있다 (instance-controlled class)
  * 인스턴스를 제어하면 싱글톤(singleton) 또는 인스턴스 생성 불가(noninstantiable) 클래스로 만들 수 있음
  * 불변 클래스에서 두 개의 동일한 인스턴스가 생기지 않도록 해줌
  * 인스턴스의 동일 여부 확인할 때 equals(Object) 대신 ==연산자 사용 가능 

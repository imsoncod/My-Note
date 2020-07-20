# JVM vs JRE vs JDK

<br>

## JVM(Java Virtual Machine)

자바 가상머신이 줄임말로 자바 프로그램 등을 컴파일하여 만들어진 코드를 실행해주는 가상머신이다.

JVM으로 인해 JAVA는 어떤 운영체제에서도 동일한 형태로 실행시킬 수 있는 특징이 있다.

<br>

## JRE(Java Runtime Environment)

컴파일된 자바 프로그램을 실행시킬 수 있는 자바 환경

JVM이 자바 프로그램을 동작시킬 때 필요한 라이브러리 파일들과 기타 파일들을 가지고 있다.

개발자가 아니라 JAVA언어로 만들어진 프로그램을 사용하는 사용자라면 JRE만 설치하면 된다.

<br>

## JDK(Java Development Kit)

자바 개발도구의 줄임말로 JRE + 자바 프로그래밍에 필요한 도구(javac, jvm) 등을 포함한다.

<br>

## 흐름

Java코드 -> JDK컴파일(.class 생성) -> JVM -> 실행

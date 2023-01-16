# MVC, MVVM, MVW, MVP란?

소프트웨어 설계와 관련된 디자인패턴

## MVC

Model, View, Controller의 약자로 디자인 패턴 중 하나이다.

1. Model: 애플리케이션의 정보, 데이터 등을 나타내며 가공을 책임지는 컴포넌트이다.
2. View: 사용자 인터페이스 요소를 나타낸다.
3. Contorller: 데이터와 사용자인터페이스 요소들을 잇는 다리역할을 한다.

## MVP

Model, View, Presentor의 약자로 디자인 패턴 중 하나이다.

1. Model: 애플리케이션의 정보, 데이터 등을 나타내며 가공을 책임지는 컴포넌트이다.
2. View: 사용자 인터페이스 요소를 나타낸다.
3. Presentor: View는 Model에 직접 데이터를 요청하지 않고 Presentor를 통해 데이털르 얻게 되는데 이때 Presentor는 Model에 데이터를 요청하고 응답받은 데이터를 View에 전달한다.

## MVVM

Model View, View Model의 약자로 디자인 패턴 중 하나이다.

1. Model: 애플리케이션의 정보, 데이터 등을 나타내며 가공을 책임지는 컴포넌트이다.
2. View: 사용자 인터페이스 요소를 나타낸다. 이때 다른 디자인 패턴과는 달리 사용자 인터페이스를 나타낼 때 View Model에 Data Binding을 통해 변경된 데이터를 사용자 화면에 뿌려준다.
3. View Model: View로 부터 전달받은 Action을 통해 Model에 데이터를 요쳥하고 응답받은 데이터를 가공 및 저장하며 가공된 데이터를 View와 Data Binding한다.

# 리액트란?

페이스북에서 만든 라이브러리로 오직 V만 신경 쓰는 라이브러리이다.

## Virtual DOM

DOM을 추상화하여 변경점을 찾아 최소한의 연산으로 DOM을 업데이트하는 가상의 트리

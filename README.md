## :pushpin: cafesmartorder
>카페 스마트 오더 프로그램 


</br>

### 1. 제작기간&참여 인원
* 2022.9.13. ~ 2022.9.19.   
* 팀프로젝트(3인)

</br>

### 2. 사용기술
* JAVA11   
* ORACLE
* WindowBuilder

</br>

### 3. ERD
<img src="img/ERD.jpg" width="600" height="300">

</br>

### 4. 핵심기능

>Client ( 회원가입 및 탈퇴, 장바구니, 주문, 포인트 적립, 인기메뉴 확인 )   
- 메뉴를 조회할 수 있다.
- 원하는 메뉴를 담을 수 있다.
- 담은 메뉴들을 결제할 수 있다.
- 포인트를 적립하고 5개가 모일 시 아메리카노 무료 쿠폰을 받을 수 있다.
- 매출 기반 인기 메뉴를 확인할 수 있다.
- 회원 가입 및 탈퇴를 할 수 있다.

<details>
<summary>상세설명 펼치기</summary>
</br>

#### 4-1. 전체흐름

<img src="img/프로젝트구조.png" width="600" height="300">
</br>
</br>

#### 4-2. Connection ✔️ [코드확인](https://github.com/jin4618/cafesmartorder/blob/4ce1b1a21be77d43740bc542db8b9ff976e21174/src/connection/Connection1.java#L3-L23)
-	JDBC를 활용한 OracleDB 연결

</br>

#### 4-3. 메인 화면

<img src="img/Main.png" width="600" height="300">
</br>

-	오늘의 인기메뉴</br>
    - 결제할 때마다 주문 내역을 ‘total’ 테이블에 메뉴와 수량을 저장하여 가장 많이 팔린 메뉴 출력 ✔️ [코드확인](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/total/TotalDAO.java#L41-L64)

-	회원생성 버튼</br>
-	메뉴 버튼</br>
-	결제 버튼</br>
-	취소 버튼 (추가한 메뉴들 초기화)</br>
-	회원 탈퇴 버튼</br>

</br>

#### 4-4. 회원가입 및 탈퇴 ✔️ [코드확인](https://github.com/jin4618/cafesmartorder/blob/77eb38e12f8fdd77cdf12e8586e39f07396a9116/src/member/MemberDAO.java#L20-L52)

<img src="img/Member.png" width="600" height="300">
</br>

- 가입 번호(핸드폰 번호 뒤 4자리) 입력 => DB에서 'member1' 테이블에 insert
- 회원 번호(핸드폰 번호 뒤 4자리) 입력 => DB에서 'member1' 테이블에서 데이터를 조회하여 delete
</br>

#### 4-5. 주문

<img src="img/Order.png" width="600" height="300">
</br>

-	수량 입력
-	메뉴 추가할 때마다 추가한 메뉴, 수량 및 가격 출력 => DB에서 ‘CafeTable’ 테이블에 저장 ✔️ [코드확인](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/order/OrderDAO.java#L130-L196) </br>
</br>

#### 4-6. 포인트 적립 및 결제

<img src="img/Pay.png" width="600" height="300">
</br>

- 총 주문 내역 출력 -> DB에 ‘CafeTable’ 테이블에서 데이터를 조회하여 불러옴 ✔️ [코드확인](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/menu/Count.java#L78-L94) </br>
-	Yes 버튼 누를 시 포인트 적립 창으로 이동</br>
- 포인트 적립을 원할 경우 회원 번호를 입력 받아 적립</br>
    - DB에 'member1' 테이블에서 데이터를 조회하고 회원번호가 맞는지 확인 ✔️ [코드확인](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/point/PointDAO.java#L56-L77) </br>
    - 현재 포인트 내역 출력 / 5개 모일 시 아메리카노 쿠폰 증정 (포인트 초기화) ✔️ [View](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/point/Point_1.java#L52-L91) ✔️ [DAO](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/point/PointDAO.java#L81-L121)</br>
- 적립을 원하지 않을 경우 결제만 진행</br>
</br>

#### 4-7. 유효성 검사 ✔️ [수량 코드확인](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/menu/Menu.java#L273-L292) ✔️ [회원번호 코드확인](https://github.com/jin4618/cafesmartorder/blob/671901a5c604aab8d1ec731f939ebe9a8a34c87f/src/menu/Menu.java#L577-L596)

<img src="img/validations.png" width="600" height="300">
</br>

- 입력 받아야 하는 Data 조건이 맞지 않을 경우 다시 입력 받음
</br>



</details>

</br>

### 5. 느낀점
처음하는 프로젝트라서 주제부터 스토리보드, 구현까지 감을 잡기가 어려웠던 것 같습니다. 그리고 팀원 또한 4명에서 시작하여 한 팀원이 가정사로 빠지게 되면서 시간적 여유 또한 부족하게 느껴졌습니다. 그래도 남은 팀원들끼리 하나하나 맞춰가며 서로 어려운 부분이 있으면 도와주고 같이 찾아 보며 좀 더 완성도 있게 프로젝트를 마무리할 수 있었습니다. 어려움은 있었지만 그것은 잠깐일 뿐 프로젝트가 완성되어 가는 과정과 팀원들과 함께 소통하며 작업을 진행하는 상황들이 흥미롭고 뿌듯했습니다.

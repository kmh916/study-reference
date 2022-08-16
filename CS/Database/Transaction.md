# Transaction

### - [[10분 테코톡] 🌼 예지니어스의 트랜잭션](https://youtu.be/e9PC0sroCzc)

<details>
<summary>내용 정리</summary>
<div markdown="1">       

### 트랜잭션이란
A가 B에게 만원을 계좌이체를 했을때 A의 잔액에서 만원이 차감되는 SQL 쿼리와 B의 잔액이 만원 증가하는
SQL 쿼리가 발생할것이다. 하지만 두 쿼리 사이에서 시스템상의 장애가 발생한다면 A의 잔액에서 만원이
차감됬는데 B의 잔액은 그대로인 상황이 발생할 수 있다. 이러한 상황등을 예방하고 데이터 베이스의 
안정성을 보장하기 위해 고안된 기술이 트랜잭션이다. 트랜잭션은 다수의 쿼리를 하나의 논리적 작업단위로 묶은 것이다.  
  
  
### 트랜잭션의 성질
`ACID` : 트랜잭션이 안전하게 수행된다는 것을 보장하기 위한 성질
  
- Atomicity(원자성) : 트랜잭션은 DB에 모두 반영되거나, 전혀 반영되지 않아야 한다. 
  (All or Nothing)
- Consistency(일관성) : 트랜잭션 작업 처리 결과는 항상 일관성 있어야 한다.
  데이터베이스는 항상 일관된 상태로 유지되어야 한다. -> 트랜잭션의 작업 처리 결과가 
  데이터베이스의 제약 조건을 위반 해서는 안되고 트랜잭션 완료후 데이터베이스의 무결성이
  유지되어야 한다.
- Isolation(격리성) : 각각의 트랜잭션은 서로 간섭없이 독립적으로 이루어져야 한다.
- Durability(지속성) : 성공적으로 수행된 트랜잭션은 영구히 데이터베이스에 반영되어야 한다.
 
## 트랜잭션 격리 수준
동시에 DB에 접근할 때 그 접근을 어떻게 제어할지에 대한 설정 수준(레벨)

- READ-UNCOMMITTED : 커밋 전의 트랜잭션의 데이터 변경 내용을 다른 트랜잭션이 읽는 것을 허용한다.
  ![image](https://user-images.githubusercontent.com/94831670/184796384-37940a19-9811-41ca-802b-243eda2bf442.png)

- READ-COMMITTED : 커밋이 완료된 트랜잭션의 변경사항만 다른 트랜잭션에서 조회 가능
  ![image](https://user-images.githubusercontent.com/94831670/184796515-ad53acf2-bbf7-4bc6-a9f6-06586899050e.png)

- REPEATABLE-READ : 트랜잭션 범위 내에서 조회한 내용이 항상 동일함을 보장
  ![image](https://user-images.githubusercontent.com/94831670/184796637-55d46e5d-ff11-4ea9-9a38-e99816129397.png)

- SERIALIZABLE : 한 트랜잭션에서 사용하는 데이터를 다른 트랜잭션에서 접근 불가

  
## 트랜잭션 격리 수준에 따른 문제점
![image](https://user-images.githubusercontent.com/94831670/184796922-c5696b27-ddb5-40de-b526-0e760e721b82.png)

- Dirty Read : 다른 트랜잭션에서 커밋되지 않은 값을 읽었는데 해당 트랜잭션이 
  롤백된 경우 해당 문제가 발생한다.
  ![image](https://user-images.githubusercontent.com/94831670/184797902-2eda95e9-cd89-4a56-baa3-6aa1c7f3cd9d.png)

- Non-Repeateable Read : 한 트랜잭션 내에서 조회의 결과가 다른 문제점
  ![image](https://user-images.githubusercontent.com/94831670/184798238-b37d157e-5a78-4d29-96ba-376092d9eff9.png)

- Phantom Read : Non-Repeateable Read 의 한 종류로 한 트랜잭션 내에서 조회의 Row 갯수가 다른 문제점
 ![image](https://user-images.githubusercontent.com/94831670/184798500-93483102-415b-48dc-b9ec-3c02b752eedf.png)

## 트랜잭션 전파 타입
트랜잭션의 경계에서 트랜잭션이 어떻게 동작할 것인가. 
  
 <details>
<summary>경계???</summary>
<div markdown="1">
  
  ![image](https://user-images.githubusercontent.com/94831670/184798875-0f7c05da-5731-4824-984f-13b849cd532f.png)

  </div>
</details>
  
 ![image](https://user-images.githubusercontent.com/94831670/184798745-dbd87d08-0835-49eb-a000-54bfbc7c1348.png)

</div>
</details>

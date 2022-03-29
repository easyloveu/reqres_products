**Req/Res 연동**

1. 주문 생성
http localhost:8081/orders productId=1 quantity=3 customerId="sunghan.lee@hanwha.com" customerName="Lee" customerAddr="seoul"
![image](https://user-images.githubusercontent.com/102270635/160507856-40a69811-e01d-430f-a2f5-e2313cc2608b.png)



2. 배송 확인
http localhost:8082/deliveries
![image](https://user-images.githubusercontent.com/102270635/160507815-d00e48e4-dcc1-47c6-acd3-750818c1047a.png)


3. 부하 툴을 사용하여 주문 생성
siege -c2 -t10S  -v --content-type "application/json" 'http://localhost:8081/orders POST {"productId":2, "quantity":1}

<부하 전>
![image](https://user-images.githubusercontent.com/102270635/160507930-4c679192-cbf2-419b-a275-30496384bcd1.png)

<부하 후>
![image](https://user-images.githubusercontent.com/102270635/160507945-1201381f-8d3e-4787-8c26-7810eded63b0.png)


4. fallback 처리를 하여 유연하게 대처
<fallback 처리 후>
![image](https://user-images.githubusercontent.com/102270635/160507989-f5f3462d-ca00-4aa8-8310-73dce9b3d419.png)



**이벤트 Publish / Subscribe**

1. order 서비스의 이벤트 Publish
http localhost:8081/orders productId=1 productName="MSA Book" qty=3

OrderApplication에서 Run 실행 후 kafka Consumer에서 이벤트 확인
![image](https://user-images.githubusercontent.com/102270635/160508329-a9fb56ef-f5cb-4213-aaad-abb944889c7c.png)

![image](https://user-images.githubusercontent.com/102270635/160508343-4d4dff99-49a0-4e09-82cf-42f458cd6d02.png)

![image](https://user-images.githubusercontent.com/102270635/160508354-68279a2a-6799-4778-aa30-262fb7747a7d.png)





**CQRS 패턴에 의한 데이터 통합**
1. Kafka 확인
![image](https://user-images.githubusercontent.com/102270635/160508295-8632d410-26ae-4230-86f8-821c1919ad45.png)


2. 주문상태 배송상태 조회
![image](https://user-images.githubusercontent.com/102270635/160508299-ab906a1e-5a87-4fd4-9886-c38132625027.png)








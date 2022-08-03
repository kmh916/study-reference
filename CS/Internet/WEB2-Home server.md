# WEB2-Home server (22.08.03)[[youtube]](https://youtube.com/playlist?list=PLuHgQVnccGMA52uRBmSwqcvtI5IMoFclJ)
<details>
<summary>1. 수업소개</summary>
<div markdown="1">

본 강의는 나의 컴퓨터를 서버로 이용하는 방법을 배우고 그 과정에서 필요한 많은 네트워크 기술들을 학습하게 됩니다. 
  
### IPv4 
전화를 하기 위해서 전화번호가 필요한 것 처럼 인터넷에 연결된 컴퓨터들간에 
통신을 위해서는 IP(Internet Protocol) 주소가 필요하다
1980년대 초 IPv4(인터넷 프로토콜 버전 4)를 개발하였고 해당 프로토콜에서 IP주소는 
x.x.x.x의 형태 (0≤x≤255 인 정수) 로 나타내며 4,294,967,296개의 주소를 표현 할수 있다(256의 4승)
  
### IPv6의 등장
기술의 발전으로 인터넷에 연결되는 컴퓨터의 갯수가 증가하고 IPv4의 주소 체계로는 부족하게 되고 
IPv6 가 등장한다 IPv6의 주소체계는 xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx 이며
(x는 하나의 16진수) 16^32 개의 주소를 표현할 수 있다 

### 공유기
IPv4 를 IPv6로 한번에 완전히 대체하는 것은
어려운 일이기 때문에 하나의 IPv4 주소를 나누어 사용할 수 있게하는 '공유기'가 만들어졌다
</div>
</details>

<details>
<summary>2. 공유기(Router)</summary>
<div markdown="1">

### 공유기 
우리는 가정에서 인터넷을 사용하기 위해서 통신사와 계약을 하고 외부에서 들어온 인터넷 선을 이용해서 
인터넷을 사용한다. 하지만 인터넷의 연결할 기기의 갯수는 여러개고 인터넷 선을 
그만큼 연결할 수 없기 때문에 하나의 인터넷 연결을 여러개로 나누어 줄 수 있는 공유기를 사용한다.
  
### WAN & LAN
이때 외부에서 공유기로 연결된 인터넷 망을 WAN(Wide Area Network) 공유기에서 기기로 연결된 
인터넷 망을  LAN(Local Area Network) 이라고 하며 
WAN 의 IP 주소를 Public IP(공인 ip) LAN 의 IP 주소를 Private IP(사설 IP) 라고 한다. 

  
### private IP 
해당 범위의 IPv4 IP 주소는 사설 IP로 사용하기로 약속되었다
![image](https://user-images.githubusercontent.com/94831670/182532253-702202f7-f2f2-4426-9947-49bc92de513f.png)

### 검증?
앞선 강의의 내용대로라면 같은 와이파이를 사용중인 노트북과 스마트폰은 같은 Public IP를 사용해야 한다.
혹시나 문제가 될까봐 올리진 못하겠는데 확인해봤더니 같은 Public IP 를 사용중이였다.


</div>
</details>

<details>
<summary>3. NAT(Network Address Translation)</summary>
<div markdown="1">
  
  ### NAT란?
  LAN에서 외부 인터넷, 예를 들어 구글에 접속하기 위해서는 나의 요청이 외부 DNS서버 까지
  도달해야 할것이다. 요청이 라우터(공유기)를 통해 DNS 서버에 도달하여 구글의 IP 주소를 
  요청할때 라우터에서는 나의 private IP를 공유기의 public IP로 변환하여 요청한다.
  이 기술을 NAT라고 한다.  
  
  ### NAT의 장점?
  - private IP가 변환되므로 외부로 부터 private IP를 감출수있다.
  - IPv4의 한정된 주소를 효과적으로 활용할 수 있다.
  
</div>
</details>

<details>
<summary>5. port</summary>
<div markdown="1">
  
나의 컴퓨터를 서버로 사용하기 위해서는 
외부에서 나의 라우터의 public IP로 들어온 요청이 나의 private IP로 연결되어야 한다.
이를 위해서는 포트 포워딩이라는 기술을 사용해야하고 포트가 무엇인지를 먼저 알아야 한다.

  ### port
  포트는 특정 네트워크나 프로세스를 식별하는 논리단위이다. 하드웨어를 컴퓨터에 연결할때 연결시키는 부분을 포트(USB 포트)라고 부르듯이
  소프트웨어에서의 포트는 네트워크상에서 특정 프로세스나 네트워크에 접근하기위한 연결 통로라고 생각하면 될 것 같다.
  
</div>
</details>

<details>
<summary>6. port forwarding</summary>
<div markdown="1">
  
  나의 라우터의 public IP로 들어온 요청이 내 컴퓨터의 private IP로 연결되기 위해서는
  public IP의 특정 포트로 들어온 요청을 나의 private IP로 포트포워딩 시켜주면 된다.
  
  ### 포트 포워딩이란?
  [위키](https://ko.wikipedia.org/wiki/%ED%8F%AC%ED%8A%B8_%ED%8F%AC%EC%9B%8C%EB%94%A9)


  
</div>
</details>

<details>
<summary>7.Dynamic & Static IP address</summary>
<div markdown="1">
  
- ISP(Internet Service Provider)는 IP 자원을 효율적으로 관리하기 위해 
고객들에게 동적으로 IP를 할당한다. -> Dynamic IP

- 해당 IP가 서버로써 동작하고 있다면 큰 문제가 발생하기 때문에 IP를 정적으로 유지시킬수 있다.
  -> Static IP
  

  예시) AWS에서 EC2 인스턴스를 생성하고 인스턴스를 부팅할때 마다 IP가 바뀌는데(Dynamic IP) 탄력적 IP(Static IP)를 연결하면 IP 주소가 고정된다.



  
</div>
</details>

</div>
</details>

<details>
<summary>8.DHCP(Dynamic Host Configuration Protocol)</summary>
<div markdown="1">
  
  ### DHCP 란?
라우터와 인터넷 기기(클라이언트)의 LAN이 연결되었을때 라우터의 DHCP Server와 
클라이언트의 DHCP Client가 서로 통신하여 라우터가 클라이언트에게 가용한 private IP를 제공한다.
이러한 통신 프로토콜을 DHCP(Dynamic Host Configuration Protocol)라고 한다.
  
 ### 맞나?
  공공장소(버스,카페,편의점 등)에서 wifi를 사용하면 특정 사이트에 접속하여 특정한 절차를 거친후에 인터넷이 사용가능한 경우가 있는데
  이게 DHCP를 사용하여 구현한 것이라고 생각이 된다.
  
  
<details>
<summary>이런거</summary>
<div markdown="1">
  
  ![image](https://user-images.githubusercontent.com/94831670/182563604-c6634e93-66d2-4caf-bc09-f5f41077d734.png)
</div>
</details>
  
</div>
</details>



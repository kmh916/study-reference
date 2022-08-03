# WEB2-Home server [[youtube]](https://youtube.com/playlist?list=PLuHgQVnccGMA52uRBmSwqcvtI5IMoFclJ)
<details>
<summary>1. 수업소개</summary>
<div markdown="1">

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

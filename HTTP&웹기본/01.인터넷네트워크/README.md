# 인터넷 네트워크

### IP(Internet Protocol, 인터넷 프로토콜)

#### IP역할

- 지정한 IP주소(= IP Address)에 데이터를 전달.
- 패킷(Packet) 이라는 통신 단위로 전달.

#### IP의 한계

- 비 연결성
  - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 일단 패킷을 전송함.
- 비 신뢰성
  - 중간에 패킷이 소실되어도 모름.
  - 전송한 패킷 순서대로 수신하지 않을 수도 있음.
- 프로그램 구분
  - 같은 IP를 사용하는 곳 에서 여러 패킷을 받으면 구분은 어떻게 할 지 모름.

#### 인터넷 프로토콜 4계층

![img](https://hongchangsub.com/content/images/2021/07/-----------2021-07-13-------11.31.58.png)

#### TCP

- Transmission Control Protocol, 전송 제어 프로토콜
- TCP는 전송계층에 속함
- 특징
  - 연결지향 -> TCP 3way handshake(가상 연결)
  - 데이터 전달 보증
  - 순서 보장
  - 즉, TCP는 신뢰할 수 있는 프로토콜로 위의 3개 특징으로 IP한계를 해결해줌.
  - 현재는 대부분 TCP를 사용하고 있음

#### 3way handshake

![3way_handshake img](https://www.usenix.org/legacy/publications/library/proceedings/bsdcon02/full_papers/lemon/lemon_html/img1.png)

    1. 클라이언트가 서버로 SYN(접속 요청)을 보냄
    2. 서버가 요청을 받으면 클라이언트에 SYN(서버가 클라이언트에 접속 요청)과 ACK(클라이언트가 서버로 접속 요청에 대한 수락)를 보냄
    3. 클라이언트가 서버로 ACK(서버가 클라이언트로 접속 요청에 대한 수락)을 보냄

- 3way handshake에서 연결이 된 것은 실제로 연결된 것이 아닌, 논리적으로 클라이언트와 서버가 연결이 된 것을 뜻한다.

#### 데이터 전달 보증

![데이터전달보증Img](https://velog.velcdn.com/images%2Fgparkkii%2Fpost%2F6396dcdd-13f4-4331-b086-5d032c6895b8%2FF30E5F25-EA34-4A15-9356-A69B1886B2E2.jpeg)

- 클라이언트가 데이터를 전송하고, 서버가 데이터를 받았다는 회신을 클라이언트가 받지 못한다면 데이터 전송에 문제가 생김을 알 수 있음.

#### 순서 보장

![순서보장Img](https://velog.velcdn.com/images%2Fgparkkii%2Fpost%2Fb2238e9c-c5ae-4951-b6eb-4e88dd84d571%2F56A360D5-8E73-4C6B-BC6A-35201B9639FC.jpeg)

#### TCP/IP 패킷 정보

![TCP/IP패킷정보Img](https://velog.velcdn.com/images%2Fgparkkii%2Fpost%2F39b64dde-b3bf-4ada-a495-c25a8eb78251%2F68228607-2BDA-472D-877E-9348CED5DEFD.jpeg)

| DATA : 내가 보내려는 데이터

- TCP/IP 패킷 정보는 내가 보내려는 데이터를 감싸는 TCP 정보, TCP 정보를 감싸는 IP Packet으로 되어 있다.
- TCP SEGMENT덕분에 IP 한계인 비 연결성, 비 신뢰성을 해결할 수 있다.

#### UDP

- User Datagram Protocol, 사용자 데이터그램 프로토콜
- 기능이 거의 없음(= 하얀 도화지로 비유함)
- TCP의 3way handshake 없음
- 데이터 전달 보증 없음
- 순서 보장 없음
- 데이터 전달 및 순서를 보장하진 않지만 단순하고 빠름
- 특징
  - IP와 비슷 + Port 추가 + checksum 추가
  - 애플리케이션에서 추가 작업 필요

#### Port

- 같은 IP내에서 프로세스를 구분
- ex) 내가 게임, 음악 듣기 등등 여러 애플리케이션을 실행할 때 나의 IP로 여러 패킷이 오는데, 수신한 패킷이 어느 애플리케이션인지 구별하는데 사용
- Port는 0 ~ 65535 할당 가능
- 0 ~ 1023은 잘 알려진 포트로 사용하지 않는것이 좋음 (= well-known port)
- 대표적으로 알려진 포트
  - FTP - 20, 21
  - TELNET - 23
  - HTTP - 80
  - HTTPS - 443

#### DNS

- Domain Name System
- 전화번호부 같은 느낌
- 사람이 읽을 수 있는 도메인 이름(ex - www.naver.com)을 IP 주소로 변환하는 시스템
- DNS 동작 방식  
  ![DNS동작방식](https://velog.velcdn.com/images/krafftdj/post/8bc98e65-96d5-4170-81e0-5f982e816279/image.png)
      자세한 동작 방식
      1. 웹 브라우저가 해결사 서버에 요청
      2. 해결사 서버는 최상위 기관에서 관리하는 네임 서버에게 요청
      3. 최상위 기관에서 관리하는 네임 서버가 응답
      4. 해결사 서버는 .com 네임 서버에 요청
      5. .com네임 서버 응답
      6. 해결사 서버는 가비아 네임 서버에게 요청
      7. 가비아 네임 서버 응답
      8. 해결사 서버는 웹 브라우제에게 알려줌

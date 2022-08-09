# 주소창에 www.google.com을 입력하면 일어나는 일

## 1. 질문의 의도

웹 브라우저에서 사이트의 주소를 입력했을 때 어떠한 통신이 오고가는지, 어떠한 과정으로 웹페이지를 불러오고 렌더링하는지 알고있는가?

## 2. 개념

1. 사용자가 웹 브라우저를 통해 google.com을 입력하면 URL 주소 중 도메인 네임 부분을 DNS 서버에서 검색합니다.
   DNS(Domain Name System)은 사람이 읽을 수 있는 도메인(www.amazon.com)을 머신이 읽을 수 있는 IP 주소(192.0.2.44)로 변환합니다.
2. DNS서버에서 해당 도메인 네임에 해당하는 IP주소를 찾아 사용자가 입력한 URL 정보와 함께 전달합니다.
3. 브라우저는 HTTP 프로토콜을 사용하여 요청 메시지를 생성하고 HTTP 요청 메시지는 TCP/IP 프로토콜을 사용하여 서버로 전송됩니다.<br>
   TCP/IP란 컴퓨터들끼리 네트워크로 소통할때 필요한 통신규약입니다. 대표적인 것이 HTTP 프로토콜입니다. 브라우저가 IP주소를 받게 되면 IP 주소에 해당하는 서버와 connection을 빌드하게 됩니다. 브라우저는 인터넷 프로토콜을 사용해서 서버와 연결이 됩니다. 인터넷 프로토콜의 종류는 여러가지가 있지만 HTTP요청의 경우는 일반적으로 TCP를 사용합니다. 클라이언트와 서버 간의 데이터 패킷들이 오가려면 TCP connection 이 되어야 합니다. TCP/IP three-way handshake라는 프로세스를 통해 클라이언트와 서버 간의 connection이 이루어지게 됩니다.

- 클라이언트 머신이 SYN패킷을 서버에 보내고 connection을 열어달라고 물어본다.
- 서버가 새로운 connection을 시작할 수 있는 포트가 있다면 SYN/ACK패킷으로 대답을 한다.
- 클라이언트는 SYN/ACK 패킷을 서버로부터 받으면 서버에게 ACK 패킷을 보낸다.
  이 과정이 끝나면 TCP connection이 완성이 됩니다.

4. 서버는 response 메세지를 생성하여 다시 브라우저에게 데이터를 전송합니다.
5. 브라우저는 response를 받아 파싱하여 화면에 렌더링합니다.

## 3. 대답

1. 사용자가 웹 브라우저를 통해 google.com을 입력하면 URL 주소 중 도메인 네임 부분을 DNS 서버에서 검색합니다.
2. DNS서버에서 해당 도메인 네임에 해당하는 IP주소를 찾아 사용자가 입력한 URL 정보와 함께 전달합니다.
3. 브라우저는 HTTP 프로토콜을 사용하여 요청 메시지를 생성하고 HTTP 요청 메시지는 TCP/IP 프로토콜을 사용하여 서버로 전송됩니다.
4. 서버는 response 메세지를 생성하여 다시 브라우저에게 데이터를 전송합니다.
5. 브라우저는 response를 받아 파싱하여 화면에 렌더링합니다.

# 출처

- https://babycoder05.tistory.com/entry/wwwgooglecom-%EC%9D%84-%EC%A3%BC%EC%86%8C%EC%B0%BD%EC%97%90-%EC%B9%98%EB%A9%B4-%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94-%EC%9D%BC-What-happens-when-type-wwwgooglecom
- https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/what-happens-when-type-google.md

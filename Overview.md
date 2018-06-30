## Introduction
#### Features:
- JMS compliance
- Connectivity
- Client APIs
#### Why we use ActiveMQ ?
- Nếu sử dụng RPC thì client và server sẽ bị gắn chặt với nhau khiến cho quá trình phát triển hoặc maintain sẽ gặp nhiều khó khăn. ActiveMQ sẽ giải quyết được điều đó.
#### When we use ActiveMQ ?
- Heterogeneous application integration: Khi mà client có thể là C/C++, .NET, Perl, PHP... thì chúng ta nên dùng ActiveMQ.
- As a replacement for RPC
- To loosen the coupling between applications
- As the backbone of an event-driven architecture
- To improve application scalability
## MOM and JMS
#### MOM
- Là thành phần ở giữa sender và reciever giúp đảm bảo sự không phụ thuộc giữa sender và reciever.
#### JMS
- Bản thân nó không phải là MOM. Nó là abstract đứng giữa client và MOM(giống như JDBC).
##### The JMS specification:
  - JMS clients: 
    + JMS PRODUCERS.
    + JMS CONSUMERS.
  - Non-JMS clients
  - The JMS provider
  - The JMS message
  - JMS message internals:
    + Header
    + Properties
  - Message selectors
  - JMS domains
    + Point to point
    + Subcriber/ Pulisher
## ActiveMQ message storage
#### Kahadb
  ![](images/https://github.com/dungtechno92/ActiveMQ/blob/master/5.3.PNG)
  - The data logs

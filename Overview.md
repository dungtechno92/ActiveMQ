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
  - KahaDb internals:
    + The data logs: Gồm nhiều file chứa nhật ký thay đổi của message. Khi file đã đẩy, ActiveMQ sẽ tự động tạo 1 file data log mới. Khi tất cả các message của 1 file data không được trỏ đến thì file data log đó sẽ bị xóa hoặc được lưu trữ lại. Message chỉ được thêm vào cuối file nên quá trình insert rất nhanh.
    + The cache: Giữ các message khi có consumer nào tồn tại. Khi tồn tại consumer, tin nhắn sẽ được gửi đi cùng lúc nó được schedule để lưu trữ. Nếu tin nhắn được consumer lấy trong thời gian đó thì tin nhắn không cần phải được ghi vào đĩa.
    + The BTree indexes: Giữ con trỏ đến các message trong file data logs, nó duy trì FIFO data structure.
    + The redo log: Được sửa dụng khi ActiveMQ không được tắt đúng cách và còn được dùng để đảm bảo tính toàn vẹn của Btree indexes.
  ![](https://github.com/dungtechno92/ActiveMQ/blob/master/5.3.PNG)
#### Caching message
  - 

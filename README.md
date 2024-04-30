# Reflection
## 1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
- **Unary**: the client sends a single request to the server and waits for a single response. This method is suitable for scenarios where you need to send a request to the server and get back a single, relatively small response, like fetching user data.
- **Server streaming**: the client sends a single request to the server, and the server responds with a stream of messages. This method is suitable for scenarios where the server needs to send a potentially large amount of data to the client in a sequential manner, like fetching a list of items.
- **Bi-directional streaming**: allows both the client and the server to send a stream of messages to each other. This method is suitable for scenarios where real-time communication or continuous exchange of data between client and server is required, like video call.

## 2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
- **Authentication**: ensure that clients and servers are properly authenticated before allowing access to sensitive resources or data.
- **Authorization**: once clients are authenticated, enforce access control policies to ensure that clients are authorized to perform specific actions or access certain resources.
- **Data encryption**: encrypt data transmitted over the network to prevent eavesdropping and ensure confidentiality.

## 3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
One of the potential challenge that may arise is resource management. Bidirectional streaming involves maintaining long-lived connections between clients and servers, which can consume system resources (such as memory and network sockets) if not managed properly. Efficient resource management strategies, such as connection pooling, idle connection timeouts, and backpressure mechanisms, may be necessary to prevent resource exhaustion and ensure scalability.

## 4. What are the advantages and disadvantages of using the `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC services?
The advantage is that it is integrated with `tokio` library, which makes it easier to work with other `tokio` methods. The disadvantage is that the learning curve for understanding asynchronous concepts is really steep in Rust, one must understand ownership and lifetime in order to be able to use it.

## 5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
Probably do the same as in the tutorials, making `service`, `repository`, `model`, and `controller`. Although I don't know if it's actually better to implement something designed FOR JAVA in Rust. I have my doubts.

## 6. In the `MyPaymentService` implementation, what additional steps might be necessary to handle more complex payment processing logic?
Probably validation and error handling. It needs to validate whether the payment meets the required criteria or not, then handle if it don't meet the criteria with sending the appropriate gRPC status code response.

## 7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
The adoption of gRPC as a communication protocol can lead to more efficient, scalable, and maintainable distributed systems, but it also requires careful consideration of interoperability challenges and integration with existing technologies and platforms.

## 8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
HTTP/2 offers significant advantages for gRPC communication, such as multiplexing and header compression, but also introduces complexity and resource consumption. The choice between HTTP/2, HTTP/1.1, or WebSocket depends on factors such as performance requirements, compatibility considerations, and the specific use case of the application.

## 9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
While both REST APIs and gRPC offer ways to achieve real-time communication, gRPC's bidirectional streaming capabilities provide a more efficient and responsive approach for scenarios requiring continuous data exchange and low-latency communication. REST APIs, on the other hand, may require additional techniques such as long-polling or WebSocket-based approaches to achieve real-time communication, which may not be as efficient or scalable for certain use cases.

## 10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
The schema-based approach of gRPC with Protocol Buffers provides advantages in terms of type safety, efficiency, versioning, and tooling support. However, it may require more upfront effort to define schemas and manage evolution. JSON payloads in REST APIs offer flexibility and ease of use but may lack some of the benefits provided by a strict schema and efficient serialization format. The choice between gRPC and REST depends on factors such as performance requirements, development preferences, and interoperability considerations.

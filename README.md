# Module 9: High Level Networking

> #### Novrizal Airsyahputra - 2206081780 - Advance Programming B

---

1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

**ANS:**

* Unary: Client sends & receives a single request to & from the server. Suitable for simple request-response interactions (fetching data / invoking a function remotely).
* Server Streaming: Client sends a single request to the server & receives a stream of responses. Suitable when server needs to send a large amount of data back to the client (transferring files).
* Bi-directional Streaming: Both client & server establish a stream, allowing to send multiple messages back and forth asynchronously. Suitable for real-time communication scenarios, such as chat application scenario (parties need to send & receive messages concurrently).

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

**ANS:**

* Authentication: Verify the identity of clients with JSON web tokens or OAuth2.
* Authorization: Defining access control rules to restrict clients' access to certain functionalities.
* Data Encryption: Ensure data confidentiality & integrity during transmission with using TLS or Transport Layer Security.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?

**ANS:**

* Concurrency: Manage the concurrent streams & handle synchronization between client-server.
* Error Handling: Dealing with errors that may occur during streaming. For example, network interruptions / unexpected disconnections.
* Resource Management: Ensuring efficient resource utilization, especially in scenarios with a large number of concurrent streams.

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?

**ANS:**

Advantages:

* Integration Convenience: ReceiverStream provides a convenient way to convert a Rust Receiver into a stream, enabling integration with tokio's async runtime (simplifies asynchronous stream handling in gRPC services).
* Increased Productivity: Utilizing ReceiverStream can accelerate development as it allows developers to focus on core business logic w/o spending time on the implementation details of stream handling.
* Support for Asynchronous Paradigm: By leveraging ReceiverStream, gRPC services can be designed to operate asynchronously. Enhancing their performance and scalability in handling multiple requests concurrently.

Disadvantages:

* Additional Overhead: ReceiverStream may introduce additional overhead, especially when dealing with large volumes of data. This could result in higher memory usage / decreased performance in scenarios with high loads.
* Flexibility Limitations: ReceiverStream may limit flexibility in stream handling, especially if business requirements necessitate more complex custom implementations / specific features not provided by ReceiverStream.

5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?

**ANS:**

* Modularity: Organize code into reusable modules & separating concerns -> service definitions, request handlers, and data models.
* Dependency Injection: Design services to be easily injectable, facilitating testing and future enhancements.
* Error Handling: Implement robust error handling mechanisms to handle failures gracefully & provide meaningful feedback to clients.

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?

**ANS:**

* Transaction Management: Implement transactional safeguards to ensure data consistency & integrity.
* Error Recovery: Handle edge cases & errors gracefully, w/ appropriate fallback mechanisms & error reporting.
* Scalability: Design systems to scale efficiently to handle varying loads and spikes in transaction volume.

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?

**ANS:**

* Interoperability: gRPC's language-agnostic nature facilitates communication between services written in different programming languages, promoting interoperability.
* Efficiency: HTTP/2's multiplexing and header compression features improve performance and resource utilization compared to HTTP/1.1, enhancing overall system efficiency.
* Service Contracts: Protobuf's schema-based approach promotes clearer service contracts.

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?

**ANS:**

Advantages of HTTP/2 for gRPC:

* Multiplexing: Allowing multiple requests and responses to be sent concurrently over a single connection. This reduces latency and improves efficiency.
* Header Compression: Reducing overhead and improving network utilization compared to HTTP/1.1. This is beneficial for performance.
* Server Push: Enabling servers to proactively send resources to clients without waiting for a request. This can improve page load times & enhance user experience in web applications.

Disadvantages of HTTP/2 for gRPC:

* Complexity: This could potentially increase development and maintenance overhead.
* Compatibility: This could necessitate additional configuration or fallback mechanisms for compatibility with older systems.
* Resource Consumption: Particularly in scenarios with a large number of concurrent connections. This could affect server resource utilization and scalability.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?

**ANS:**

* REST APIs: Follow a request-response model where clients initiate requests and wait for responses. Real-time communication typically relies on polling / long polling techniques. This may lead to latency and overhead.
* gRPC: Supports bidirectional streaming, allowing for real-time communication between clients and servers. This enables more responsive interactions.

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?

**ANS:**

* Protocol Buffers: Provide a more structured and efficient way to define data schemas, leading to smaller message sizes & faster serialization/deserialization compared to JSON. Additionally, Protobuf's schema evolution capabilities facilitate backward & forward compatibility.
* JSON in REST APIs: Offers flexibility and readability but may result in larger payloads and slower processing due to parsing overhead. Also, can lead to compatibility issues when evolving APIs over time because of JSON.

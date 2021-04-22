# realworld-javascript

Algorithms and techniques I developed (while standing on the shoulders of giants).

I was creating a node/express backend and needed to serialize incoming requests where the processing of each request might require a short pause to wait for an asynchronous process to complete. Processing multiple requests simultaneousl would be a disaster due to shared data. It is the nature of these things that responses cannot always be sent immediately so occasioally briefly holding incoming requests is likely not going to cause significant latency.

If a response could be sent back without waiting for processing then the incoming requests could have been stuffed into an array and pulled out one at a time. However even that presents a small challenge since node is single-threaded. Blocking and waiting would completely hang the system as the single thread would not be able to handle incoming requests.

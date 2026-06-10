---
name: realtime-communication
description: "Build real-time, bidirectional features using WebSockets, SSE, or WebRTC. Implement chat, live notifications, and collaborative tools."
---

# Real-time Communication Skill

Implement low-latency, bidirectional communication for interactive applications.

## When to Use

Use this skill when the user wants to:
- Build chat applications
- Implement live notifications or live-updating dashboards
- Create collaborative tools (e.g., shared whiteboards, collaborative editing)
- Build real-time presence indicators (online/offline status)
- Implement live sports scores or stock tickers
- Build peer-to-peer video or audio calls (WebRTC)

## Technologies

### 1. WebSockets
- **Concept**: Full-duplex, persistent connection over a single TCP connection.
- **Best For**: Bidirectional communication where both client and server need to push data frequently.
- **Protocols**: `ws://` (unencrypted) or `wss://` (encrypted).

### 2. Socket.io
- **Concept**: A library built on top of WebSockets that provides fallbacks (like long polling), auto-reconnection, and "rooms" for easy broadcasting.
- **Best For**: Rapid development of complex real-time features where reliability and ease of use are priorities.

### 3. Server-Sent Events (SSE)
- **Concept**: A standard allowing servers to push data to web pages over HTTP. It is unidirectional (server to client).
- **Best For**: Scenarios where only the server needs to push updates (e.g., live feeds, notifications) and client-to-server communication is done via standard HTTP requests.

### 4. WebRTC (Web Real-Time Communication)
- **Concept**: A peer-to-peer protocol for real-time audio, video, and generic data transfer between browsers.
- **Best For**: Low-latency video/audio calls and peer-to-peer file sharing.

## Implementation Examples

### FastAPI (Python) - WebSocket Example
```python
from fastapi import FastAPI, WebSocket, WebSocketDisconnect

app = FastAPI()

class ConnectionManager:
    def __init__(self):
        self.active_connections: list[WebSocket] = []

    async def connect(self, websocket: WebSocket):
        await websocket.accept()
        self.active_connections.append(websocket)

    def disconnect(self, websocket: WebSocket):
        self.active_connections.remove(websocket)

    async def send_personal_message(self, message: str, websocket: WebSocket):
        await websocket.send_text(message)

    async def broadcast(self, message: str):
        for connection in self.active_connections:
            await connection.send_text(message)

manager = ConnectionManager()

@app.websocket("/ws/{client_id}")
async def websocket_endpoint(websocket: WebSocket, client_id: int):
    await manager.connect(websocket)
    try:
        while True:
            data = await websocket.receive_text()
            await manager.broadcast(f"Client #{client_id} says: {data}")
    except WebSocketDisconnect:
        manager.disconnect(websocket)
        await manager.broadcast(f"Client #{client_id} left the chat")
```

### gRPC - Real-time Streaming Example (Conceptual)
```protobuf
syntax = "proto3";

service ChatService {
  // Bidirectional streaming
  rpc ChatStream (stream ChatMessage) returns (stream ChatMessage);
}

message ChatMessage {
  string user = 1;
  string text = 2;
}
```

## Implementation Patterns

### Connection Management
- **Heartbeat (Ping/Pong)**: Periodically send small packets to keep the connection alive and detect silent failures.
- **Auto-Reconnection**: Implement exponential backoff on the client side to reconnect if the connection drops.

### Scalability
- **Pub/Sub Mechanism**: Use a backend like Redis to synchronize messages across multiple server instances.
- **Load Balancing**: Use sticky sessions if using WebSockets with certain load balancers (to ensure the handshake and connection land on the same server).

### Security
- **Authentication**: Authenticate connections (e.g., via JWT in the connection handshake).
- **Authorization**: Use "rooms" or "channels" to ensure users only receive messages they are authorized to see.
- **Sanitization**: Always sanitize incoming messages to prevent Cross-Site Scripting (XSS).

## Common Pitfalls

- **Connection Leaks**: Forgetting to close/remove connections when a client disconnects, leading to memory leaks and performance degradation.
- **Scalability Bottlenecks**: Relying on in-memory state for connections without a distributed pub/sub (like Redis) to sync across multiple servers.
- **Lack of Reconnection Logic**: Assuming the connection will stay alive forever; clients must be able to recover from network drops.
- **Unsecured WebSockets**: Using `ws://` instead of `wss://`, exposing data to man-in-the-middle attacks.

## Deliverables

- Real-time communication implementation (WebSockets, Socket.io, SSE, or WebRTC)
- Connection management logic (connect, disconnect, reconnect)
- Message handling and broadcasting logic
- Security implementation (Auth, Sanitization, Authorization)
- Real-time features (Chat, Notifications, Presence, etc.)
- Integration tests for real-time flows

## Quality Checklist

- [ ] Connections are authenticated and authorized.
- [ ] Auto-reconnection with exponential backoff is implemented on the client.
- [ ] Heartbeat/Ping-Pong is used to maintain connection health.
- [ ] Messages are sanitized to prevent injection attacks.
- [ ] Scalability is considered (e.g., using Redis for multi-server setups).
- [ ] Documentation of the real-time events and message formats is provided.

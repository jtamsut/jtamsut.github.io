---
layout: post
title: "Introduction to WebRTC"
categories: ruby objects classes
---

RTC = "Real Time Communication"

WebRTC implements three APIs

* `MediaStream` (a.k.a, `getUserMedia`)
* `RTCPeerConnection`
* `RTCDataChannel`
*

# Adding Real Time Features

WebSockets are a useful tool for creating real-time web applications. <b>Real-time</b> web applications allow users or clients to receive information as it's being published. For example, consider a hypothetical chat application that has many users. When a user submits a chat message every other user receives that message. Here is a schematic of this chat application:

<img src="https://docs.google.com/drawings/d/1uQhYHoa5g5XqoW8thBf9VHD0elrIpkG7wH8oBmXKIo4/pub?w=960&amp;h=720">

There is one source of data that all clients are updating when they submit a chat. When one user submits a chat message it is sent to the database (i.e., the contents of the database is updated). A situation like this necessitates the need for some sort of persistent, bi-directional line of communication between the server and a client: a WebSocket. WebSockets allow for <b>full-duplex</b> communication. A full-duplex communication system allows for two parties to communicate with one another at the same time. Modern day cellphones allow for full-duplex communication. When you call someone on your cellphone both you, and the person you called, can talk simultaneously.

#### The WebSocket Protocol

A WebSocket is established over a single TCP socket. TCP, or Transmission Control Protocol, is the set of rules for how two entities on the Internet form a connection between one another and how they exchange data. WebSockets are initially created via a <b>handshake</b> done via HTTP. Handshaking refers to the process of two parties on a network establishing communication parameters before normal communication can begin. After a communication line is open between a client and server the

### A Brief Discussion of the Client Server Model




WebSockets provide a persistent connection between a client and a server that both parties can use to begin communicating with one another.

#### Socket.IO

SocketIO is composed of 2 parts:

  * a server that integrates with the Node HTTP Server
  * a client library that loads on the browser side

Web sockets allow for a long-held single TCP socket connection to be established between the client and server which allows for bi-driectional messages to be instantly distributed with little overhead.

The Internet was conceived to all that dynamic.

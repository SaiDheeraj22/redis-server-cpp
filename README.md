# My C++ Redis Server

A lightweight Redis-like in-memory data store implemented in C++.

This project was built to understand how an in-memory database works internally, including TCP networking, request parsing, concurrent clients, data structures, key expiration, and persistence.

---

## Overview

This project implements a Redis-like server that allows clients to store and retrieve data through a TCP connection using the Redis Serialization Protocol (RESP).

The server runs on port `6379` by default and stores data primarily in memory for fast access.

It supports:

- String key-value storage
- Lists
- Hashes
- RESP request parsing
- Multiple concurrent clients
- Key expiration
- Database persistence
- Basic Redis commands

---

## Features

### String Operations

- `SET`
- `GET`
- `KEYS`
- `TYPE`
- `DEL`
- `UNLINK`
- `EXPIRE`
- `RENAME`

### List Operations

- `LGET`
- `LLEN`
- `LPUSH`
- `RPUSH`
- `LPOP`
- `RPOP`
- `LREM`
- `LINDEX`
- `LSET`

### Hash Operations

- `HSET`
- `HGET`
- `HEXISTS`
- `HDEL`
- `HKEYS`
- `HVALS`
- `HLEN`
- `HGETALL`
- `HMSET`

### Other Commands

- `PING`
- `ECHO`
- `FLUSHALL`

---

## Architecture

The basic request flow is:

```text
Client
   |
   | TCP Connection
   v
Redis Server
   |
   v
RESP Parser
   |
   v
Command Handler
   |
   v
Redis Database
   |
   +-------------------+
   |                   |
   v                   v
String Store       List Store
   |
   v
Hash Store

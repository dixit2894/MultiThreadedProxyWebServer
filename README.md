# HTTP Proxy Server

A lightweight HTTP proxy server implemented in C, supporting GET requests, caching, and multithreaded client handling.

## Features
- Handles HTTP GET requests (HTTP/1.0 and HTTP/1.1)
- Caches responses with Least Recently Used (LRU) eviction
- Supports concurrent clients using POSIX threads
- Thread-safe cache with mutex and semaphore synchronization
- Returns standard HTTP error responses (400, 403, 404, 500, 501, 505)

## Requirements
- C compiler (e.g., GCC)
- POSIX-compliant system (Linux, macOS, etc.)
- `proxy_parse.h` library for HTTP request parsing

## Compilation
Compile the code with pthread support:
```bash
gcc -o proxy proxy.c -pthread
```
Run the server with an optional port (default: 8080):
```bash 
./proxy 8080
```
To test:
Set your browser’s proxy to localhost:8080.
Visit a site (e.g., http://example.com).
Check console for cache hits and errors.

## Configuration
- Edit these in proxy.c and recompile:
- MAX_BYTES: Request/response size (4096 bytes)
- MAX_CLIENTS: Concurrent clients (400)
- MAX_SIZE: Cache size (200 MB)
- MAX_ELEMENT_SIZE: Max cache entry (10 MB)
- port_number: Default port (8080)

## Limitation
- Only supports GET requests.
- No HTTPS or other HTTP methods.

## Example Workflow
- Save proxy.c and README.md.
- Compile: gcc -o proxy proxy.c -pthread.
- Run: ./proxy 8080.
- Configure browser proxy to localhost:8080.
- Test with http://example.com.

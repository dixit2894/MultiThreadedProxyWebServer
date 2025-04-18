Proxy Server
A simple HTTP proxy server implemented in C that supports GET requests, caching, and multithreading.
Features

Handles HTTP GET requests
Caches responses to improve performance
Supports multiple clients using threads
Implements LRU (Least Recently Used) cache eviction
Error handling for common HTTP status codes (400, 403, 404, etc.)

Requirements

C compiler (e.g., gcc)
POSIX-compliant system (Linux, macOS, etc.)
proxy_parse.h library for parsing HTTP requests

Compilation
gcc -o proxy proxy.c -pthread

Usage
Run the proxy server with an optional port number (default is 8080):
./proxy [port]

Example:
./proxy 8080

Configuration

MAX_BYTES: Maximum size of request/response (4096 bytes)
MAX_CLIENTS: Maximum concurrent clients (400)
MAX_SIZE: Cache size (200 MB)
MAX_ELEMENT_SIZE: Maximum size of a cache element (10 MB)

How It Works

Listens for client connections on the specified port.
Creates a thread for each client to handle requests.
Parses HTTP GET requests and forwards them to the target server.
Caches responses and serves them for matching requests.
Uses semaphores and mutexes for thread safety.

Notes

Only supports HTTP/1.0 and HTTP/1.1 GET requests.
Cache uses LRU policy to evict old entries when full.
Ensure proxy_parse.h is available for compilation.


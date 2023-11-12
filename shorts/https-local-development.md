## Why
 - I want to run https server for my system. The system should run in https to ensure all feature like set cookie working.
 - Don't want dev code like:
```golang
if (isDev()) {
  // Start server with local cert files
}
```

## How
 - Use /etc/hosts to override dns with my custome domain
 - Use caddy as reverse-proxy to support https
https://www.codingforentrepreneurs.com/blog/https-on-localhost-with-caddy/

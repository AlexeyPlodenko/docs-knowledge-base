Add container healthcheck rule to Dockerfile:
```Dockerfile
HEALTHCHECK --interval=30s --timeout=10s --retries=3 CMD curl -f http://localhost:8000/health || exit 1
```

Do not run your app from the root. Use the user provided in the FROM container or create your own:
```Dockerfile
RUN adduser --disabled-password --gecos "" appuser
USER appuser
```

Because labels do not guarantee immutability of the Docker image, we should pin the version with a SHA hash:
```Dockerfile
FROM alpine:3.21@sha256:a8560b36e8b8210634f77d9f7f9efd7ffa463e380b75e2e74aff4511df3ef88c
```

Docker official best practices https://docs.docker.com/build/building/best-practices/

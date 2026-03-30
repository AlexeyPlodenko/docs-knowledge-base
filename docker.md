Add container healthcheck rule to Dockerfile
```Dockerfile
HEALTHCHECK --interval=30s --timeout=10s --retries=3 CMD curl -f http://localhost:8000/health || exit 1
```

Do not run your app from the root. Use the user provided in the FROM container or create your own
```Dockerfile
RUN adduser --disabled-password --gecos "" appuser
USER appuser
```

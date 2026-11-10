# lane2-exec releases

Releases of `lane2-exec`, the entrypoint for services deployed to Railway with Lane 2.

Each release includes:

- `lane2-exec-linux-amd64` (Railway runs linux/amd64)
- `SHA256SUMS`

Make it the service's entrypoint, ahead of the app's own command:

```dockerfile
ADD --chmod=755 --checksum=sha256:a7313e301fc7f4e7889575ed88738c3d0d3b4f7d3ca52817a4f40d15c122a862 \
  https://github.com/mrq-vibes/lane2-exec-releases/releases/download/v1.0.1/lane2-exec-linux-amd64 \
  /usr/local/bin/lane2-exec
ENTRYPOINT ["lane2-exec", "--"]
CMD ["node", "server.js"]
```

The build fails if the download doesn't match the checksum.

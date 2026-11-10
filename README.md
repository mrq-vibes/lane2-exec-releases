# lane2-exec releases

Releases of `lane2-exec`, the entrypoint for services deployed to Railway with Lane 2.

Each release includes:

- `lane2-exec-linux-amd64` (Railway runs linux/amd64)
- `SHA256SUMS`

Make it the service's entrypoint, ahead of the app's own command:

```dockerfile
ADD --chmod=755 --checksum=sha256:79970e5c69bc13f81312733825362a0977997d48a4db7e16e9f0531c138e5365 \
  https://github.com/mrq-vibes/lane2-exec-releases/releases/download/v1.0.0/lane2-exec-linux-amd64 \
  /usr/local/bin/lane2-exec
ENTRYPOINT ["lane2-exec", "--"]
CMD ["node", "server.js"]
```

The build fails if the download doesn't match the checksum.

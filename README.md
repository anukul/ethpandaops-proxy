ethpandaops-proxy

---

a simple nginx reverse proxy to attach authentication headers to ethpandaops requests 

- copy `env.template` to `.env` and populate with your credentials
- run `docker compose up`

now,

```sh
$ curl localhost/prysm.mainnet/eth/v1/node/version
```

is reverse proxied to

```sh
$ curl https://prysm.mainnet.ethpandaops.io/eth/v1/node/version \
  --header "CF-Access-Client-Id: $CF_ACCESS_CLIENT_ID" \
  --header "CF-Access-Client-Secret: $CF_ACCESS_CLIENT_SECRET"
```

and similarly for other requests of the format `localhost/foo/bar` to `foo.ethpandaops.io/bar`

# Generate Data-At-Rest encryption keys

```
for i in {1..5}; do echo "$i;$(openssl rand -hex 32)" >> keyfile;  done; \
openssl rand -hex 128 > keyfile.key && \
openssl enc -aes-256-cbc -md sha1 -pass file:keyfile.key -in keyfile -out keyfile.enc
```

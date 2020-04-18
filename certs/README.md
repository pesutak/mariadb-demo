# Certs genaration

## Generate A CA Certificate

```
openssl genrsa 2048 > ca-key.pem && \
openssl req -new -x509 -nodes -days 365000 -subj "/C=SK/ST=PP/L=Poprad/O=Excalibur/CN=XCLBR CA Server" -key ca-key.pem -out ca-cert.pem
```

## Generate A Server Certificate

```
openssl req -newkey rsa:2048 -days 365000 -nodes -keyout server-key.pem -out server-req.pem -subj "/C=SK/ST=PP/L=Poprad/O=Excalibur/CN=XCLBR DB Server" && \
openssl rsa -in server-key.pem -out server-key.pem && \
openssl x509 -req -in server-req.pem -days 365000 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out server-cert.pem
```

## Generate A Client Certificate

```
openssl req -newkey rsa:2048 -days 365000 -nodes -keyout client-key.pem -out client-req.pem  -subj "/C=SK/ST=PP/L=Poprad/O=Excalibur/CN=XCLBR Client" && \
openssl rsa -in client-key.pem -out client-key.pem && \
openssl x509 -req -in client-req.pem -days 365000 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out client-cert.pem
```

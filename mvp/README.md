## Setup

1. `envoy -c min_sidecar.yaml --log-level debug` - port 10006
1. `envoy -c min_igw.yaml --log-level debug` - port 8183
1. `https_proxy=http://localhost:8183 curl -vvv -o /dev/null https://www.google.com` works
1. `https_proxy=http://localhost:10006 curl -vvv -o /dev/null https://www.google.com` does not work, can CONNECT, but cannot TLS handshake `curl: (35) LibreSSL/3.3.6: error:1404B42E:SSL routines:ST_CONNECT:tlsv1 alert protocol version`

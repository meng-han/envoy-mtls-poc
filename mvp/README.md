## Setup

1. `envoy -c min_sidecar.yaml --log-level debug` - port 10006
1. `envoy -c min_igw.yaml --log-level debug` - port 8183
1. `https_proxy=http://localhost:10006 curl -vvv -o /dev/null https://www.google.com`
    * curl -> sidecar -> igw -> internet
    * sidecar forwards CONNECT to IGW, between them, mTLS is established
    * IGW CONNECTs with internet
    * TCP establishes between curl and internet
    * curl establishes TLS with Internet and exchanges packets

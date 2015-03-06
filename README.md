# kube-register

Register Kubernetes Kubelet machines with the Kubernetes API server using Fleet data.

## Usage

```
kube-register -metadata="kubelet=true" -fleet-endpoint="http://127.0.0.1:4002" -api-endpoint="http://127.0.0.1:8080"
```

## Building

```
mkdir -p "${GOPATH}/src/github.com/kelseyhightower"
cd "${GOPATH}/src/github.com/kelseyhightower"
git clone https://github.com/kelseyhightower/kube-register.git
cd kube-register
godep go build .
```

Slightly smaller binary.

```
CGO_ENABLED=0 GOOS=linux godep go build -a -tags netgo -ldflags '-w' .
```

To build the binary inside a docker container.

```
docker run -v $SRC:/opt/kube-register -i -t google/golang /bin/bash -c "cd /opt/kube-register && go get github.com/tools/godep && godep go build ."
```

Where $SRC is the absolute path to the kube-register directory.

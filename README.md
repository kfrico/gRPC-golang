# gRPC-golang
gRPC-golang


### 環境設定

#### 安裝protobuf

&nbsp;
自行編譯protobuf

```sh
mkdir tmp
cd tmp
git clone https://github.com/google/protobuf
cd protobuf
./autogen.sh
./configure
make
make check
sudo make install
```

&nbsp;

編譯有問題可能需要安裝 autoconf automake libtool

```sh
sudo apt-get install autoconf automake libtool
```

&nbsp;

或是直接下載編譯好的檔案
[https://github.com/google/protobuf/releases](https://github.com/google/protobuf/releases)
解壓縮完bin的protoc複製到

```sh
/usr/local/bin/
```

&nbsp;

include資料夾底下的檔案複製到

```sh
/usr/local/include/
```

&nbsp;

#### 下載proto套件

```sh
go get -u github.com/golang/protobuf/proto
```

&nbsp;

#### 下載protoc轉go的套件

```sh
go get -u github.com/golang/protobuf/protoc-gen-go
```

&nbsp;

#### 下載gRPC轉gateway的套件

```sh
go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway
go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger
```

&nbsp;

#### proto編譯成grpc go檔

```sh
protoc -I/usr/local/include -I. -I$GOPATH/src -I helloworld/ -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis helloworld/helloworld.proto --go_out=plugins=grpc:.
```

&nbsp;

#### proto編譯成grpc gateway go檔

```sh
protoc -I/usr/local/include -I. -I$GOPATH/src -I helloworld/ -I$GOPATH/src/github.com/grpc-ecosystem/grpc-gateway/third_party/googleapis helloworld/helloworld.proto --grpc-gateway_out=logtostderr=true:.
```


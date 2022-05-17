# dockerfile常见指令

```dockerfile
#构建镜像
#文件名DockerFile
FROM golang:1.18

ENV GO111MODULE=on \
    CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64 \
    GOPROXY="https://goproxy.io"
# 指定shell语句运行在哪个路径下（镜像内）
WORKDIR /data
# 将宿主机内的文件拷贝到镜像中去 与ADD相似 但ADD还可以是url 
COPY ./ /data
# 运行shell语句 构建时运行
RUN go build .
# 声明服务端口
EXPOSE 9999
# 启动容器时命令 （容器运行的时候）与ENTRYPOINT相似 如果ENTRYPOINT不是json数组形式，以ENTRYPOINT为准，如果两者都是，则前后拼接成一句指令

CMD

```

```shell
# -t命名镜像 .表示dockerfile在当前目录下
docker build -t [镜像名] .
```


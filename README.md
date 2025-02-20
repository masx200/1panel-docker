# 1panel-docker

获取最新版本号的接口改成了

https://api.github.com/repos/1Panel-dev/1Panel/releases/latest

# 说明

基于[okxlin/docker-1panel](https://github.com/okxlin/docker-1panel)修改了下几个文件，仅解决不使用/opt 目录时直接使用应用商店安装应用报错的问题，其他的使用方式和问题都同原项目。
刚玩 github，不太懂规则，如果有什么做的不对的，欢迎指正。

## 另外我也会针对一些常用好玩的应用做一些视频教程和文字教程，大家可以关注下小 up，B 站：masx200，公众号：masx200999，什么值得买：masx200。

# docker-compose 使用方式

创建 docker-compose.yml 文件，将以下内容中的/xxxx/opt 替换成你自己的应用安装路径，注意三个/xxxx/opt 都需要修改成一样的。

PANEL_PORT=10086 #自定义端口号，不设置默认为 10086

PANEL_ENTRANCE=masx200 #自定义安全入口，不设置默认为 entrance

PANEL_USERNAME=masx200 #自定义用户名，不设置默认为 1panel

PANEL_PASSWORD=masx200999 #自定义登录密码，不设置默认为 1panel_password

文件上传到本地后执行 docker compose up -d

```huggingface-cli
services:
  1panel:
    container_name: 1panel # 容器名
    restart: always
    network_mode: "host"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /var/lib/docker/volumes:/var/lib/docker/volumes
      - /xxxx/opt:/xxxx/opt # 文件存储映射
      - ./root:/root  # 可选的文件存储映射
    environment:
      - TZ=Asia/Shanghai  # 时区设置
      - PANEL_BASE_DIR=/xxxx/opt
      - PANEL_PORT=10086
      - PANEL_ENTRANCE=masx200
      - PANEL_USERNAME=masx200
      - PANEL_PASSWORD=masx200999
    image: docker.io/masx200/1panel:latest
    labels:
      createdBy: "Apps"
```

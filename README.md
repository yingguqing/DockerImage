[![GitHub](https://img.shields.io/github/license/wukongdaily/DockerTarBuilder.svg?label=LICENSE&logo=github&logoColor=%20)](https://github.com/yingguqing/DockerImagePusher/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/yingguqing/DockerImagePusher.svg?style=flat&logo=appveyor&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/yingguqing/DockerImagePusher.svg?style=flat&logo=appveyor&label=Forks&logo=github)

## 🤔 这是什么？
它是一个工作流。可快速构建linux平台的amd64(x86_64)和arm64的docker镜像。使用manifest合并后，
使用Github Action将国外的linux平台的Docker镜像转存到阿里云私有仓库，供国内服务器使用，免费易用<br>
- 支持DockerHub, gcr.io, k8s.io, ghcr.io等任意仓库<br>
- 支持最大40GB的大型镜像<br>
- 使用阿里云的官方线路，速度快<br>
- 拉取amd64(x86_64)和arm64架构，使用manifest合并。

## 阿里云参数
启用个人实例，创建一个命名空间（**ALIYUN_NAME_SPACE**）<br>
访问凭证–>获取环境变量<br>
用户名（**ALIYUN_REGISTRY_USER**)<br>
密码（**ALIYUN_REGISTRY_PASSWORD**)<br>
仓库地址（**ALIYUN_REGISTRY**）<br>

## 打包镜像

Action目录下，使用以下脚本。

- `amd64.yml`
- `arm64.yml`

## 感谢

打包脚本是从[DockerTarBuilder](https://github.com/wukongdaily/DockerTarBuilder)复制过来的。

部分灵感借鉴[docker_image_pusher](https://github.com/tech-shrimp/docker_image_pusher)

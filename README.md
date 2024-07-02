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
- 打包镜像上传到`github`，在action界面下载。
- 打包镜像，直接上传到个人服务器上。

## 个人Docker仓库

Action目录下`Docker`工作流，可以选择相应的云和构架。需要分别配置以下参数。

### 阿里云参数

启用个人实例，创建一个命名空间（**ALIYUN_NAME_SPACE**）<br>
访问凭证–>获取环境变量<br>
用户名（**ALIYUN_REGISTRY_USER**)<br>
密码（**ALIYUN_REGISTRY_PASSWORD**)<br>
仓库地址（**ALIYUN_REGISTRY**）<br>

### 腾讯云参数

创建一个命名空间（**TENCENT_NAME_SPACE**）<br>
访问用个人实例–>登录实例<br>
用户名（**TENCENT_REGISTRY_USER**) 一串数字<br>
密码（**TENCENT_REGISTRY_PASSWORD**)<br>
仓库地址（**TENCENT_REGISTRY**）<br>

## 打包镜像

Action目录下`Download`工作流，可以选择相应的镜像构架，然后自动打包。

- `amd64`
- `arm64`

## 上传到服务器

Action目录下`Upload`工作流，目前不支持同时上传到多个服务器。因个有需要，配置了两个服务器上传地址，每次只能上传到一个服务端。

本人服务端使用`svenstaro/miniserve`的上传服务，上传链接：`-H "Authorization: Basic (用户名:密码)base64" "https://服务器上传服务URL/upload?path={保存路径，主目录用/}" -F "path=@{文件完整路径}"`。配置参数：

`Authorization`：`Basic (用户名:密码)base64`

`UPLOADURL`：`https://服务器上传服务URL/upload?path={保存路径，主目录用/}`

`ipv6`：`http://[2409:8a55:116:1111:1111:1111:1111:5]:4534/upload?path=/`

**注意**：如果域名是托管在`cloudflare`上，上传URL直接填写`IP`和`端口`。因为`cloudflare`对上传文件大小有限制，普通用户单个文件最大`100M`。或者对大文件切分后再上传。大文件镜像最好还是使用`阿里云`或`腾讯云`的镜像仓库。

## 感谢

打包脚本是从[DockerTarBuilder](https://github.com/wukongdaily/DockerTarBuilder)复制过来的。

部分灵感借鉴[docker_image_pusher](https://github.com/tech-shrimp/docker_image_pusher)

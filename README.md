# maven 在线实验环境  

## 软件简介

Apache Maven是一个软件项目管理和理解工具。基于项目对象模型（POM）的概念，Maven可以从中央信息管理项目的构建，报告和文档。

所属类别是开发工具

License:APACHE LICENSE, VERSION 2.0

特点：

方便，使用简单

## 软件官网

http://maven.apache.org/

## Dockerfile 使用方法

### 如何使用
在Maven项目中创建一个Docker文件
```
FROM maven:3.2-jdk-7-onbuild
CMD ["do-something-with-built-packages"]
```
将这个文件放在你项目的根目录，旁边是pom.xml。

此映像包含多个ONBUILD触发器，应该是您需要引导的所有触发器。构建将COPY . /usr/src/app和RUN mvn install。

然后，您可以构建并运行映像：
```
$ docker build -t my-maven .
$ docker run -it --name my-maven-script my-maven
```
### 运行一个Maven命令
对于许多简单的项目，您可能会发现写一个完整的不方便Dockerfile。在这种情况下，您可以直接使用Maven Docker映像运行Maven项目，将Maven命令传递给docker run：
```
$ docker run -it --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3.2-jdk-7 mvn clean install
```
## 资源链接

- http://maven.apache.org/

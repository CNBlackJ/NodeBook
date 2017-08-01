# Docker

## 常用命令

- 批量删除容器（container）
	- `docker rm $(docker ps -a -q) -f`
- 批量删除镜像（images）
	- `docker rmi $(docker images | grep -E '<image name>' | awk '{print $3}') -f`
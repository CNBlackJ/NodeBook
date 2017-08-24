# Docker

## 常用命令

- 批量删除容器（container）
	- `docker rm $(docker ps -a -q) -f`
- 批量删除镜像（images）
	- `docker rmi $(docker images | grep -E '<image name>' | awk '{print $3}') -f`
	- `docker rmi $(docker images -q <image name>)`
- 查看虚悬镜像(dangling image)
  - dangling image: REPOSITORY = <none> & TAG = <none>
  - `docker images -f dangling=true`
  - 批量删除dangling image: `docker rmi $(docker images -q -f dangling=true)`


### 挂载数据卷

- `docker run -it -v $(pwd):/var/local/app ubuntu`
  - `-v source:target`, source&target：absolute path(绝对路径)
 
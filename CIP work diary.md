# CIP work diary
## Week 1 
### Docker
#### Basic commands
docker file => image
```shell
$ docker build -t image_name:tag .
```
image => container
```shell
$ docker run image_name:tag
```
顯示有哪些 container 在執行 & 查看 images
```shell
$ docker ps -a && docker images -a
```
進入 container 看有哪些資料夾、檔案或是要修改檔案
(-it: 等到 container 執行完成 / bash: 在 container 中開啟terminal)

```shell
$ docker exec -it container_name bash
```
停止 container & 重啟 container (container_name or ID)

```shell
$ docker stop container_name && docker start container_name
```
移除 container & image
```shell
$ docker rm -f container_name && docker rmi image_name
```
#### Jupyter support
run the image and create notebook
``` bash
$ docker run -it -p 8888:8888 --ipc=host [ufoym/deepo] jupyter notebook --no-browser --ip=0.0.0.0 --allow-root --NotebookApp.token= --notebook-dir='/root'
```

connect the notebook via http://localhost:8888/

### Git

<img src="C:\NCCU\109semester\109-2\國泰CIP\notes\Hahow for Business07：46.png" style="zoom:80%;" />

#### Basic commands
```shell
$ git config --global user.name ""
$ git config --global user.email ""
```
對存在的資料夾做版控

```shell
$ git init
```
查看當前狀態
```shell
$ git status
```
將所有當前檔案放入git保管
```shell
$ git add .
```
輸入註解，將保管檔案送出
```shell
$ git commit -m "First commit"
```
顯示commit資訊及註解
```shell
$ git log [file]
```
當新增、刪除、修改檔案或變更檔名後想要同步上git
並顯示更改過程
```shell
$ git add .
```
刪除git上資料
```shell
$ git rm
```
#### Git資料模型

<img src="C:\NCCU\109semester\109-2\國泰CIP\notes\Hahow for Business00：49.png" style="zoom:80%;" />

比較修改前後的檔案內容(還沒add、commit更新上去)
```shell
$ git diff [file]
```
顯示commit修改紀錄(press q to quit)

```shell
$ git show [commitID]
```
#### Github
整合本地repository到Github repository (新增 origin 雲端資料庫)
```shell
$ git remote add origin https://github.com/106207411/hahow-git.git
```
查看同步狀態
```shell
$ git remote show origin
```
將master資料(目前所在分支)第一次上傳到origin資料庫
```shell
$ git push -u origin master
```
下載repository(第一次完整複製)
```shell
$ git clone [url]
```
更新本地repository
並下載至工作目錄(fetch 沒有)
```shell
$ git pull [url]
```
Example (token is recommended in future)

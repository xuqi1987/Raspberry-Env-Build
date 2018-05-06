## 折腾树莓派 m

###  安装Docker

	curl -sSL https://get.docker.com | sh

###  安装docker-compose
	pip install docker-compose
	sudo apt-get -y install python-pip
	sudo pip2 install -U pip
	sudo pip2 install docker-compose
	
### 挂载网络磁盘

	sudo apt-get install smbfs smbclient
	sudo apt-get install samba samba-common-bin
	sudo apt-get install nfs-common   
	sudo mount -t cifs //192.168.1.101/sda1/onecloud/tddownload /home/pi/data/ -o username=guest,password=
	
### 安装文件管理 ownCloud(失败)

	mkdir -p ~/ownCloud/apps ~/ownCloud/config 
	ln -s ~/data ~/ownCloud/data
	cd ~/ownCloud 
	
	sudo docker run  --name myownCloud -p 8083:80 -v $PWD/apps:/var/www/html/apps -v $PWD/config:/var/www/html/config -v $PWD/data:/var/www/html/data -d owncloud:8.1
	
### 安装filebrowser
	mkdir -p  ~/filebrowser
	ln -s ~/data ~/filebrowser/data
	cd ~/filebrowser
	docker run -d --name myfilebrowser -v $PWD/data:/srv -p 8085:80 hacdias/filebrowser

启用
	
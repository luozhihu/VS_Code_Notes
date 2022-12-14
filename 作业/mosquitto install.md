# 安装依赖
```
apt install -y wget tar gcc g++ cmake libssl-dev
wget https://mosquitto.org/files/source/mosquitto-1.3.5.tar.gz
tar -zxvf mosquitto-1.3.5.tar.gz
cd mosquitto-1.3.5
mkdir build
cd build
cmake ..
make && make install
```
# 创建用户
```
sudo cp pwfile.example pwfile
sudo mosquitto_passwd -c pwfile t1
mosquitto_passwd -b pwfile t2 123456
sudo mosquitto_passwd -b pwfile t2 123456
```
# mosquitto ---配置SSL/TLS

```
mkdir myCA　
wget https://github.com/owntracks/tools/raw/master/TLS/generate-CA.sh
bash ./generate-CA.sh
bash ./generate-CA.sh client myclient
```
# 启动服务
```
mosquitto -c /home/luozhihu/mosquitto-1.3.5/mosquitto.conf

mosquitto_sub -u t2 -P luozhihu -t "test" -p 8883 --cafile /home/luozhihu/myCA/ca.crt --cert /home/luozhihu/myCA/myclient.crt --key /home/luozhihu/myCA/myclient.key

mosquitto_pub -u luo -P luozhihu123 -t "test" -p 8883 --cafile /home/luozhihu/myCA/ca.crt --cert /home/luozhihu/myCA/myclient.crt --key /home/luozhihu/myCA/myclient.key -m "wolaila"
```
# 参考文档

https://blog.csdn.net/JKL852qaz/article/details/84034252

https://blog.csdn.net/wuspeng/article/details/119217225

https://www.cnblogs.com/saryli/p/9821343.html
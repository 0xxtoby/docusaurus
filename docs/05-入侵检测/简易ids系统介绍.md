## 一、配置与运行

#### 运行

server运行

```
#server配置文件api/ids.toml
#~/web/
pip install -r requirements.txt
python3 manage.py runserver 127.0.0.1:8000
```

agent运行

```
python3 agent.py
```

配置

```
#erver配置文件api/ids.toml
```

![image-20220507205333453](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204v34833j20go0abq3r.jpg)

```
#agent配置文件 config.toml
```

![image-20220507205504871](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204wo85ipj20gi0cndgf.jpg)

## 二、文件结构

![image-20220507201427717](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h203qevzrnj20fg0lz752.jpg)

## 二、设计架构

![image-20220507204442801](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204lw1vwkj20sb0gkmz2.jpg)

## 三、server代码

### 1、sever-agent通信

使用Django框架，通过http协议传输信息

##### agent 使用data_dic类构造requests 与服务器进行信息通信

![image-20220507193501815](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h202ldo6ilj20ki0acdgp.jpg)

##### sever使用Djangoweb框架处理请求，将接收到的信息交给中心控制器类进行处理

![image-20220507193240433](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h202ixdvb0j20h207lq3j.jpg)

### 2、ControlCenter类 控制中心

过程函数根据request中的tpye参数选择不同的模块处理文件数据

![image-20220507201909776](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h203vb15soj20pd0o9whg.jpg)

#### 1）web日志分析主函数

![image-20220507202503570](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2041frakmj20xe098jsq.jpg)

#### 2）pcap包解析分析主函数

![image-20220507202847291](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2045bo18pj20um0oxn25.jpg)

#### 3）系统日志分析主函数

![image-20220507203114882](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2047vw1x2j20vc0ltdil.jpg)

### 3、AlarmInfo_list 告警类

![image-20220507203321419](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204a2hoe7j20v60km76q.jpg)

## 四、agent代码

#### 1、data_dic 类用request将日志文件传输给服务器

![image-20220507204903732](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204qey4snj20p60idmys.jpg)

#### 2、不同类型日志信息扫描

![image-20220507205724373](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204z3idtrj20n50mdgn1.jpg)

#### 3、定时运行

![image-20220507205632730](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h204y7gsckj20gs0at3yr.jpg)

## 五、展示

##### 1、开启服务端

![image-20220507205817284](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h20500ad5mj20qc08at9e.jpg)

##### 2、agent运行

定时运行上传日志

显示服务器返回信息

![image-20220507205926956](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h20517wwppj20ls08lmxt.jpg)

##### 3、服务器接受agent文件自动运行 检测威胁 

![image-20220507210059421](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2052u6fevj21cv0nxwky.jpg)

##### 4、存入数据库

![image-20220507210409842](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h20565483yj21580sm46s.jpg)



##### 5、告警日志

![image-20220507210146054](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2053nz4mij21f60qh7ik.jpg)

##### 5、web端展示

admin admin 登录

![image-20220507210234296](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2054h7l29j21fc0mh418.jpg)

##### 告警信息展示

![image-20220507210449862](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2056tpdckj21ha0sb42k.jpg)

##### 详细告警信息

![image-20220507210517766](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2057b087jj21gz0qcteh.jpg)

![image-20220507210538643](https://tobyjpghub-1258737888.cos.ap-shanghai.myqcloud.com/e6c9d24ely1h2057o2azhj21h80sg0wc.jpg)
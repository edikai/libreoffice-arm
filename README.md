# Libreoffice7.5.3.2-arm

Libreoffice arm架构运行程序

# 运行环境
系统架构：arm-鲲鹏

操作系统：麒麟v10sp2 

<img width="897" height="354" alt="image" src="https://github.com/user-attachments/assets/34b643d0-8ed2-47d3-a727-c0c7038c41dd" />

<img width="896" height="189" alt="image" src="https://github.com/user-attachments/assets/0d2ece43-185a-4914-abe5-daa7d568eb31" />

# 下载
https://github.com/edikai/libreoffice-arm/releases

<img width="1215" height="504" alt="image" src="https://github.com/user-attachments/assets/9b7d7b8a-0f4d-4187-bb7e-9e09dacb7f94" />

`libreoffice7.5.3.2-arm.zip` ： Libreoffice7.5.3.2 运行程序
  
`libxslt-1.1.32-7.ky10.aarch64.rpm` ： libxslt 包
# 安装
## 将 `libreoffice7.5.3.2-arm.zip` 上传到服务器 /opt 目录并解压

```JavaScript
unzip libreoffice7.5.3.2-arm.zip
cd libreoffice7.5.3.2-arm/program/
# 赋予执行权限
find . -maxdepth 1 -type f ! -name "*.*" ! -name "*.so*" -exec chmod +x {} \;
chmod +x *.py
chmod +x *.bin *-gdb.py
```
执行完上述操作，在 `/opt/libreoffice7.5.3.2-arm/program/` 目录下验证
```JavaScript
./soffice --version
# 正确输出： LibreOfficeDev 7.1.7.0.0 f6db54d2dd7de5b227cb766575f4b0cb7bbf5184
```
## 转换文件测试
```JavaScript
# 准备测试文件
echo "Test Document" > /data/test.txt
# 转换测试 （大概率会出现下面的错误）
./soffice --headless --convert-to pdf /data/test.txt --outdir /data/
./soffice --headless --convert-to pdf /data/test1.pptx --outdir /data/
```
$\color{red} {错误信息：} $
```diff
terminate called after throwing an instance of 'com::sun::star::uno::DeploymentException'
Application Error
```
## 错误处理
将 `libxslt-1.1.32-7.ky10.aarch64.rpm` 上传到服务器并安装，安装完成后在测试就没问题了
```JavaScript
yum install -y libxslt-1.1.32-7.ky10.aarch64.rpm
```

# 成功示例
<img width="1062" height="111" alt="image" src="https://github.com/user-attachments/assets/5e4c6dcb-be3c-44b8-8a0f-b7d6bffef12b" />



  

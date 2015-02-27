## 手动下载安装curl

~~~objectivec
cd /usr/local
sudo mkdir homebrew
curl -L https://github.com/mxcl/homebrew/tarball/master |  \
  sudo tar xz --strip 1 -C homebrew
cd homebrew/bin
./brew -v
file brew
cat brew | more
sudo ./brew update
~~~

如果“brew update”命令执行出错，请确保文件夹/usr/local的所有者权限是你本人而不是root：

~~~objectivec
sudo chown -R $USER /usr/local
brew update
~~~


## 环境变量设置

在".bash_profile"中更新路径配置

(注意:

手动创建这个文件:如果~下没有文件".bash_profile" 请执行：

~~~objectivec
 touch '.bash_profile'
~~~

）

编辑 '.bash_profile'加入

~~~objectivec
export PATH=$PATH:/usr/local/homebrew/bin
~~~

之后可以直接执行brew(不用./brew)


## 使用git安装

~~~objectivec
git clone https://github.com/mxcl/homebrew.git
cd homebrew/bin
cd homebrew/bin
./brew -v

./brew install wget
./brew uninstall wget
./brew searc /apache*/
~~~
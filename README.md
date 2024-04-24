# 简介

MusicalMoments 插件 API 使用 TCP Sockets 获取数据，因此需要发送 Get 请求。

你可以调用这些 API 来获取 MusicalMoments 的各种数据。

详情示例可看 MMPluginSDKExample: https://github.com/TheD0ubleC/MusicalMoments-PluginSDK/releases
# 安装依赖库
在命令行中输入以下命令即可安装:
```cmd
pip install PluginSDK
```
# 获取输入
首先需要获取脚本启动时命令行参数中的第一个参数（API 地址），如下所示：
```python
import sys

def main():
    if len(sys.argv) <= 1:
        sys.exit()
    else:
        server_address = sys.argv[1]
        return server_address

如果成功获取地址，将继续执行；否则将退出。
```
# 调用
首先需要实例化一个 PluginSDK 对象，并使用从命令行参数获取的 API 地址来创建实例化对象，如下所示：
```python
from PluginSDK import PluginSDK
```
```python
def run():
    server_address = main()
    if not server_address:
        print("API 地址未提供，程序退出。")
        return

    plugin_sdk = PluginSDK(server_address)
    mm_version = plugin_sdk.get_mm_ver()
    print(f"MM版本号: {mm_version}")

if __name__ == "__main__":
    run()
```

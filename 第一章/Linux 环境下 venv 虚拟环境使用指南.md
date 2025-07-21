## Linux 环境下 `venv` 虚拟环境使用指南

`venv` 是 Python 3.3+ 内置的虚拟环境管理工具，它能为你的每个 Python 项目创建独立的运行环境，有效避免不同项目间的依赖冲突。



### 1. 创建虚拟环境



在你希望存放项目的目录下创建虚拟环境。通常，虚拟环境会放在项目根目录下。

```Bash
# 1. 导航到你的项目目录（如果项目目录不存在，请先创建）
cd /path/to/your/project/folder
# 示例：cd ~/my_awesome_project
# mkdir ~/my_awesome_project && cd ~/my_awesome_project

# 2. 创建虚拟环境
# 推荐将环境命名为 .venv 或 env，以便一眼识别且不与项目文件混淆
python3 -m venv .venv
# 或者：python3 -m venv my_project_env

# 说明：
# python3：调用你系统中已安装的 Python 3 解释器（例如 Anaconda base 环境中的 Python）。
# -m venv：告诉 Python 运行 venv 模块。
# .venv 或 my_project_env：你为虚拟环境指定的名称，也是将要创建的文件夹名称。
```



### 2. 激活虚拟环境

在你安装包或运行代码之前，必须激活虚拟环境。

```Bash
# 激活虚拟环境
source .venv/bin/activate
# 如果你命名为 my_project_env：source my_project_env/bin/activate

# 确认激活：
# 激活成功后，你的命令提示符前面会显示虚拟环境的名称，例如：
# (.venv) user@host:~/my_awesome_project$
```



### 3. 在虚拟环境中安装 Python 包

激活环境后，`pip` 会将包安装到当前激活的虚拟环境中。

``` Bash
# 安装单个包
pip install package_name
# 示例：pip install requests

# 安装特定版本的包
pip install package_name==version_number
# 示例：pip install pandas==1.3.5

# 批量安装 (推荐：从 requirements.txt 文件安装所有依赖)
# 假设你的项目根目录下有一个 requirements.txt 文件
pip install -r requirements.txt
```



### 4. 查看已安装的包

要查看当前虚拟环境中安装了哪些包。

```Bash
pip list
# 或者只看你直接安装的包 (不包括依赖)：
# pip freeze
```



### 5. 生成项目依赖列表

当你项目完成或想分享依赖时，可以生成 `requirements.txt` 文件。

```Bash
pip freeze > requirements.txt
# 这个命令会将当前虚拟环境中所有已安装的包及其精确版本写入 requirements.txt 文件。
# 例如：
# numpy==1.24.4
# pandas==1.3.5
# requests==2.31.0
```



### 6. 运行 Python 脚本

在激活的虚拟环境中，可以直接运行你的 Python 脚本。

```Bash
python your_script.py
```



### 7. 退出虚拟环境

当你完成工作或想切换到另一个环境时。

```Bash
deactivate
# 退出后，命令提示符会恢复到之前的状态，例如 (base) 或默认系统提示符。
```



### 8. 删除虚拟环境

如果你不再需要某个虚拟环境，可以直接删除其文件夹。

```bash
# 确保你已经退出了要删除的虚拟环境
deactivate

# 导航到包含虚拟环境文件夹的父目录
cd /path/to/your/project/folder

# 删除虚拟环境文件夹
rm -rf .venv
# 或者：rm -rf my_project_env

# 警告：rm -rf 命令是强制递归删除，请务必确认你在正确的目录下执行，以免误删重要文件。
```
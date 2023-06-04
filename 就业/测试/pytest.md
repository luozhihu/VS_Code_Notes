配合selenium可以进行自动化测试
## 初始化清除
- 模块级别
  - setup_module(),teardown_module()
- 类级别
  - setup_class(),teardown_class()
- 方法级别
  - setup_method,teardown_method
- 目录级别
  - 需要初始化的目录下面创建 一个名为 conftest.py 
## 挑选用例执行
- 指定模块
  - pytest cases\登录\test_错误登录.py
- 指定目录
  - pytest cases1  cases2\登录
- 指定函数或类
  - pytest cases\登录\test_错误登录.py::Test_错误密码
- 根据名字
  - -k
- 根据标签
  - -m
  - 标签可以加在类上也可以加在方法上面
  - 一个类或方法可以添加多个标签
## 数据驱动

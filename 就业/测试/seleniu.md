## 选择元素基本方法
- 根据id属性选择元素
  - wd.find_element(By.ID, 'kw')
- 根据class属性、tag名选择元素
  - wd.find_elements(By.CLASS_NAME, 'animal')
  - wd.find_elements(By.TAG_NAME, 'div')
- find_element 和 find_elements 的区别
  - find_element选第一个，find_elements选多个
- 通过WebElement对象选择元素
  - element.find_elements(By.TAG_NAME, 'span')
## 输入框
element.send_keys('白月黑羽')
## 获取元素信息
- 获取元素的文本内容
  - print(element.text)
- 获取元素属性
  - print(element.get_attribute('class'))
- 获取整个元素对应的HTML
  - element.get_attribute('outerHTML')，element.get_attribute('innerHTML')
- 获取输入框里面的文字
  - element.get_attribute('value')
## css选择器
## Xpath选择器

# 🚀 Selenium Web 自动化测试

## 测试系统
OrangeHRM 在线演示系统

## 测试场景
1. 用户登录
2. 添加新员工
3. 员工信息验证

## 测试脚本
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

# 初始化浏览器
driver = webdriver.Chrome()
driver.get("https://opensource-demo.orangehrmlive.com/")

# 登录操作
driver.find_element(By.NAME, "username").send_keys("Admin")
driver.find_element(By.NAME, "password").send_keys("admin123")
driver.find_element(By.CSS_SELECTOR, "button.orangehrm-login-button").click()

# 添加新员工
driver.find_element(By.LINK_TEXT, "Add Employee").click()
driver.find_element(By.NAME, "firstName").send_keys("John")
driver.find_element(By.NAME, "lastName").send_keys("Doe")
driver.find_element(By.CSS_SELECTOR, "button[type='submit']").click()

# 验证员工添加成功
assert "John Doe" in driver.page_source

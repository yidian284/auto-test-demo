# 🔥 JMeter 接口性能测试报告

## 测试概述
- **目标 API**: reqres.in (公共测试接口)
- **测试场景**: 50 并发用户压力测试
- **测试时间**: 2024 年 6 月 10 日
- **测试者**: [yidian284]

## 测试脚本
```java
// JMeter 测试计划核心逻辑
ThreadGroup threadGroup = new ThreadGroup();
threadGroup.setNumThreads(50); // 50 并发用户
threadGroup.setRampUp(10); // 10 秒内启动

// GET 请求 - 获取用户列表
HttpSampler getUsers = new HttpSampler();
getUsers.setDomain("reqres.in");
getUsers.setPath("/api/users?page=2");
getUsers.setMethod("GET");

// POST 请求 - 创建用户
HttpSampler createUser = new HttpSampler();
createUser.setDomain("reqres.in");
createUser.setPath("/api/users");
createUser.setMethod("POST");
createUser.setPostBody("{ \"name\": \"auto\", \"job\": \"tester\" }");

// 添加结果监听器
SummaryReport summaryReport = new SummaryReport();

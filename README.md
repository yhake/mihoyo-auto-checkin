# 🌸 米游社自动签到助手

> ✅ 基于 [MihoyoBBSTools](https://github.com/Womsxd/MihoyoBBSTools) 的增强版，支持 **GitHub Actions 全自动签到**  
> 🕒 每日凌晨自动执行，无需服务器，零成本挂机

---

## 🚀 快速开始（GitHub Actions 部署）

### ① 本地镜像克隆（不带 Fork 标记）
```
git clone --mirror https://github.com/bcmdy/MihoyoBBSTools.git
cd MihoyoBBSTools.git
```

---

### ② 上传增强文件在 GitHub 新建一个空白仓库（不要选 “import” 也不要点 Fork）。

假设新仓库地址为 https://github.com/你的用户名/空白仓库.git

---

### ③ 一次性推上去
```
git push --mirror https://github.com/你的用户名/空白仓库.git
cd ..
rm -rf MihoyoBBSTools.git
```
- **注意**：push时出现报错属于正常情况

---

### 四 配置 Cookie 和 SToken 及 CAPTCHA_ENDPOINT
#### 🔑 添加 Cookie
1. 进入仓库 → `Settings` → `Secrets and variables` → `Actions`
2. 点击 **New repository secret**：
   - **Name**：`COOKIE`
   - **Value**：粘贴完整 Cookie（示例格式）：
     ```
     mid=xxx;stoken=v2_xxx=.CAE=;stuid=xxx;ltoken=xxx;ltuid=xxx;account_id=xxx;cookie_token=xxx
     ```

#### 🔐 添加 SToken
- **Name**：`STOKEN`
- **Value**：`v2_xxx=`（仅 `stoken` 值）

#### 🔐 添加 CAPTCHA_ENDPOINT
- **Name**：`CAPTCHA_ENDPOINT`
- **Value**：http://127.0.0.1:9645/pass_nine
- **说明**：```"http://127.0.0.1:9645/pass_nine"```为默认地址，docker部署即可，docker查看地址```https://hub.docker.com/r/kafuneri/captcha-tools```，自行部署，可以托管在免费的dokcer平台部署，比如koyeb、northflank、Claw Cloud Run

---

## ✅ 测试运行
1. 进入仓库 → `Actions` → `Checkin` → `Run workflow` → 点击 **Run workflow**
2. 观察日志：
   - 成功日志示例：`✅ 签到成功`
   - 失败日志会提示错误原因（如 Cookie 失效）

---

## ⏰ 定时说明
- **默认时间**：每日 **00:05 (北京时间)** 自动运行
- **修改方法**：编辑 `.github/workflows/Checkin.yml` 中的：
  ```yaml
  - cron: '5 16 * * *'  # UTC时间，北京时间+8

  
  ```

进入文件夹

使用DevContainer
- VS Code应该会自动检测到DevContainer配置
- 如果提示"Reopen in Container"，点击确认
- 或者按 `F1`，输入 "DevContainer: Reopen in Container"

修改配置文件
- 编辑 `_config.yml` 文件来设置网站基本信息
- 根据需要修改其他配置文件

实时预览
- 在本地服务器运行时，保存文件后会自动刷新页面
- jekyll serve -l -H localhost用于修改_config.yml文件
- 在浏览器中查看 http://localhost:4000 查看更改

提交更改（在本地文件夹的git bash而非container中）
git add .
git commit -m "初始化我的学术网站"
git push origin main

检查部署状态
- 在GitHub仓库中转到 Settings > Pages
- 查看部署状态，通常几分钟后生效
- 访问 https://zhoutyf.github.io 查看线上网站

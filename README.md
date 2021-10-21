## Vue 3 + Vite重写css-demo

``` 
 # clone
git clone https://github.com/https://github.com/Lck6de1p/css-demo-vite.git
```

```
# cd
cd css-demo-vite
```

```
# install dependencies
npm install
```

```
# Compiles and hot-reloads for development
npm run dev
```

```
# Compiles and minifies for production
npm run build
```

## 集成github action 自动化部署流程

**配置ci.yml文件**

ci.yml放在根目录下的.github/workflows路径下

---

内容为：

```
name: Tser CI

on:
  push:
    branches:
      - main

jobs:
  # 发布到服务器
  build-and-deploy-to-server:
    runs-on: ubuntu-18.04
    steps:
      - name: Checkout
        uses: actions/checkout@master

      - name: Setup Node.js environment
        uses: actions/setup-node@v1
        with:
          node-version: 12.x

      - name: Install Dependencies
        run: npm install
        env:
          CI: true

      - name: Build Project
        run: npm run build
        env:
          CI: true

      - name: Deploy to Server
        uses: easingthemes/ssh-deploy@v2.1.5
        env:
          SSH_PRIVATE_KEY: ${{ secrets.SSH_KEY }}
          ARGS: '-rltgoDzvO --delete'
          SOURCE: 'dist/'
          REMOTE_HOST: ${{ secrets.REMOTE_HOST }}
          REMOTE_USER: ${{ secrets.REMOTE_USER }}
          TARGET: ${{ secrets.REMOTE_TARGET }}
```

secrets所有字段和仓库地址对应的settings -> Secrets下的字段名对应

* SSH_KEY: 对应服务器私钥cat ~/.ssh/id_rsa  以
```
-----END RSA PRIVATE KEY-----
 ``` 
结尾，不要带多余空格
* REMOTE_HOST: 服务器ip地址
* REMOTE_USER: 用户名 如 root
* REMOTE_TARGET: 上传路径


具体配置查看[ssh-deploy配置](https://github.com/easingthemes/ssh-deploy)

**配置完毕后每次提交代码都会自动部署代码，并且可以在actions下查看是否部署成功**

![](http://lck6de1p.com/static/img/actions.png)





  
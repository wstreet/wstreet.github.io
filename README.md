# blog
> 采用`hexo`作为博客系统

* `master`: `blog`源码
* `gh-pages`: 编译文件

`GitHub actions`自动编译部署
```
name: Deploy
on:
  push:
    branches: master

jobs:
  Build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@master

      - name: Install Dependencies
        run: |
          npm install
          npm install hexo-cli -g

      - name: Build And Deploy...
        uses: JamesIves/github-pages-deploy-action@master
        env:
          ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
          BRANCH: gh-pages
          FOLDER: public
          BUILD_SCRIPT:  hexo generate



```

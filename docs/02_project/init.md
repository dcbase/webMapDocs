
##### 一、项目下载

1、项目下载

    git clone https://git.fpi-inc.site/product/atmosphere-products/agms/agms1.1.0/control-map-web.git

2、项目初始化

    yarn  // or npm i

3、项目运行

    yarn serve  // or npm run serve

    // 打包本地文件
    yarn build  // or npm run build


##### 二、项目初始化可能遇到问题
1、image-webpack-loader

npm直接安装可能会在运行时出现报错信息；则需要移除image-webpack-loader包，从淘宝镜像从新下载

① 移除包 `yarn remove image-webpack-loader` 或  `npm uninstall image-webpack-loader`

② 全局安装淘宝镜像

    npm install cnpm -g --registry=https://registry.npm.taobao.org

③ 使用淘宝镜像安装

    cnpm install --save-dev  image-webpack-loader 

此时再次运行`yarn serve`，应该可以看到运行成功界面

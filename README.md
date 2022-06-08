![GoIndex](https://raw.githubusercontent.com/donwa/goindex/master/themes/logo.png)  

GoIndex  
====  

这是一个 [修改版的goindex](https://github.com/yanzai/goindex) ，在 [原版goindex](https://github.com/donwa/goindex) 基础上添加了多盘支持、搜索、分页加载等功能。

`index.js` 包含 Workers 所需的代码.

## 预览

Demo: https://yanzai-goindex.java.workers.dev



多盘：  
![多盘](imgs/1.png)



搜索：  
![搜索](imgs/2.png)



分页：  
![分页](imgs/3.png)



## 更新日志

### 2020-4-28

- 添加 Basic Auth 认证，每个盘符可单独配置用户名和密码，可以保护该盘下所有子文件和子文件夹

- 支持自定义 web 界面主题色，添加了 dark_mode ; 在 `uiConfig` 中可以配置

- 原 goindex 的 .password 验证方式作为后备验证方式得以保留，但默认不开启

  以上，详见 `index.js` 中的配置项的注释。

### 2020-4-23

- 支持调用 nPlayer / MXPlayer Free / MXPlayer Pro / PotPlayer / VLC 播放，支持直接复制直链
- 简单支持 PDF 文件预览
- 可以配置是否允许其他 web 前端 cors 方式获取文件

### 2020-3-9

- flac file play support

### 2020-3-7

- 添加搜索功能，搜索结果分页增量展示，并支持跳转到对应路径浏览
- 搜索功能支持个人盘和团队盘全盘搜索
- 搜索分页大小可配置，具体见 `index.js` 注释
- 尝试解决移动端滚动到底部时的增量加载问题
- UI优化，盘符选择改为下拉框展示

### 2020-3-5

- 文件列表页分页增量加载，支持自定义分页大小，多页内容的可以缓存，配置见 `index.js` 注释
- 图片浏览页 下一张/上一张 导航
- 优化列目录时的速度

### 2020-3-4

在原版基础上修改：

- 添加多盘支持，自主设置要显示的多盘及各自密码
- 前端只修改了 material ，故不支持 classic 主题
- 配置见 `index.js` 注释
  

---



> **安装部署可以参考原版，以下摘自原版 goindex 的部署说明：**



## Demo  
material: [https://index.gd.workers.dev/](https://index.gd.workers.dev/)  
classic: [https://indexc.gd.workers.dev/](https://indexc.gd.workers.dev/)  

## Deployment  
1.Install `rclone` software locally  
2.Follow [https://rclone.org/drive/]( https://rclone.org/drive/) bind a drive  
3.Execute the command`rclone config file` to find the file `rclone.conf` path  
4.Open `rclone.conf`,find the configuration `root_folder_id` and `refresh_token`  
5.Download index.js in https://github.com/donwa/goindex and fill in root and refresh_token  
6.Deploy the code to [Cloudflare Workers](https://www.cloudflare.com/)

## Quick Deployment  
1.Open https://installen.gd.workers.dev/  
2.Auth and get the code  
3.Deploy the code to [Cloudflare Workers](https://www.cloudflare.com/)  



## About  
Cloudflare Workers allow you to write JavaScript which runs on all of Cloudflare's 150+ global data centers.  

# Ionic-QR-Scanner
Ionic 二维码扫描  由于文件过多,上传不到`github`上, 故把源码放在了百度云上面了,有需要的,可以去下载: 链接:https://pan.baidu.com/s/1i6v7nwD  密码:a967

在上班路上看了一篇文章 [ionic 使用QR Scaner 扫描](https://www.jianshu.com/p/45f8b44b9a42?utm_campaign=hugo&utm_medium=reader_share&utm_content=note),到单位后我试了, 不知道是环境版本问题,还是什么原因, ios的扫描二维码总是调不出相机, 安卓的没有问题! 超级坑......


后来`google`后,终于解决了问题
在`app.scss`中添加下面的css代码
```
html,
body.transparent-body,
.transparent-body,
.transparent-body ion-app,
.transparent-body .app-root,
.transparent-body ion-nav,
.transparent-body .ion-page,
.transparent-body .nav-decor,
.transparent-body ion-content,
.transparent-body .viewscan,
.transparent-body .fixed-content,
.transparent-body .scroll-content {
  background-color: transparent !important;
  background: transparent !important;
}
```

原来作者在`variables.scss`设置的样式就可以不用写了,最好给他删掉或者注释掉,不然上面写的代码会被层叠掉!!!

在 `scan.ts` 中 当我们离开`ScanPage`页面时,最好要把 `qrScanner`, 不然整个页面是透明的, 让人很觉得很奇怪!!!
```
  // 离开后
  ionViewDidLeave(){
    this.qrScanner.hide();
  }

  // 即将被卸载
  ionViewWillUnload(){
    this.qrScanner.hide();
  }
```


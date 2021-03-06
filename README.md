[ ![Download](https://api.bintray.com/packages/ymex/maven/banner/images/download.svg) ](https://bintray.com/ymex/maven/banner/_latestVersion)

# banner

Android Viewpager rotation control, application guide page controls, support vertical, horizontal cycle scrolling, extended from view support animation, indicator extension and so on.


Android 轮播图控件、app引导页控件，支持垂直、水平循环滚动，扩展自viewpager 支持动画，指示器扩展等。<br>

## 简介

本库有两种banner组件可供使用, 分别是 `Banner`组件 和 `RecyclerBanner`组件。<br>
`Banner`组件 基于 `ViewPager`扩展。 <br>
`RecyclerBanner`组件基于`RecyclerView`扩展。`RecyclerBanner`在内存占用和帧率上占有一定优势,
但动画效果不如`Banner`容易实现。<br>

## 效果
1、app引导页控件<br>
2、轮播图控件<br>
![gif](https://github.com/ymex/banner/blob/master/art/GIF-d.gif)<br>
3、设置翻页动画<br>
![gif](https://github.com/ymex/banner/blob/master/art/GIF-a.gif)<br>
4、自定义指示器<br>
![gif](https://github.com/ymex/banner/blob/master/art/GIF-i.gif)<br>
5、垂直滚动<br>
![gif](https://github.com/ymex/banner/blob/master/art/GIF-v.gif)<br>

## 相关属性及方法

### banner 及 RecyclerBanner部分方法
| 方法        | 解释   |
| --------   | :-----:  |
|createView()|创建banner 的布局|
|bindView()|处理banner控件元素|
|execute()|填充数据并展示|
|setOnClickBannerListener()|点击事件|
|setOrientation()|滚动方向|
|setIndicatorable()|设置指示器|
|setPageTransformer()|设置转换动画，仅Banner有此方法|


### Banner及 RecyclerBanner属性


| 属性        | 解释   |
| --------   | :-----:  |
|banner_interval|滚动间隔 (默认5000ms)|
|banner_auto_play|是否自动播放 (默认true)|
|banner_loop|是否循环滚动 (默认true)|
|banner_orientation|horizontal(默认)，vertical|

### IndicatorLayout属性
| 属性        | 解释   |
| --------   | :-----:  |
|indicator_width|indicator的宽,默认8dip|
|indicator_height|indicator的高,默认8dip|
|indicator_margin|indicator的间距,默认4dip|
|indicator_selected|选中图片或颜色|
|indicator_unselected|未选中图片或颜色|
|indicator_shape|indicator的形状，circular（默认），rectangle|
 

## 使用
banner基于viewpage 扩展，支持横向与纵向自动循环滚动。可用作 轮播图控件、app引导页控件。 
`需要 v7 的包支持`，并引入banner lib.

```
compile 'cn.ymex:banner:1.6.1'
```

1、在布局文件中加入控件,IndicatorLayout 是指示器布局,你可以随意定义其位置。如果 不使用指示器移除它就可以了。
```
<cn.ymex.widget.banner.Banner
    android:id="@+id/banner"
    android:layout_width="match_parent"
    android:layout_height="240dip"
    android:background="@color/colorAccent"
    app:banner_auto_play="true"
    app:banner_interval="5000">

    <cn.ymex.widget.banner.IndicatorLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="bottom"
        android:layout_marginBottom="8dip"
        android:gravity="center"
        app:indicator_height="8dip"
        app:indicator_width="8dip" />
</cn.ymex.widget.banner.Banner>
```

2、使用bindview加载图片资源到banner中，banner默认实现了基于AppCompatImageView的布局。

```
banner.bindView(new Banner.BindViewCallBack<AppCompatImageView,BanneModel>() {
    @Override
    public void bindView(AppCompatImageView view, BanneModel data, int position) {
        //图片加载 
        Glide.with(view.getContext())
                .load(data.getUrl())
                .into(view);
    }
}).execute(data());
```


## RecyclerBanner

`RecyclerBanner`是基于RecyclerView 扩展而来的banner 。对于大量的数据很有帮助。
`RecylerBanner` 使用方法完全同`Banner`,但个别方法不支持，如动画切换的`setPageTransformer()`。


##版本

v1.6.1
- 修复RecyclerBanner 回弹问题

v1.6.0
- 修复getCurrentItem()位置异常
- 修复IndicatorLayout使用图片时宽高失控
- 增加默认指示器indicator_shape 属性 
- 重构部分方法

v1.5.0
- 重构Banner
- 增加RecyclerBanner

v1.x.x
- banner ~

## 感谢：

- RecyclerViewPager： https://github.com/lsjwzh/RecyclerViewPager


License
-------

    Copyright 2017 ymex.cn

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
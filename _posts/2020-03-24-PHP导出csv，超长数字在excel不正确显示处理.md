---
layout:     post                    # 使用的布局（不需要改）
title:      PHP导出csv,超长数字处理         # 标题 
subtitle:   拼接“'”或者"\t"  #副标题
date:       2020-03-24              # 时间
author:     August                      # 作者
header-img: img/post-bg-2015.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - PHP
---

## PHP导出为CSV，超长数字处理
> 拼接'或者"\t"不可见字符

#### 问题描述
  导出的原始订单号，长度超过15位，后边4位显示为0。
  
#### 处理结果
  经过查询和测试，发现两种可行方案
  1. 原始订单号前拼接 '
  2. 原始订单号后边拼接 "\t"
  ```
 <?php
    $fp = fopen('test.csv', 'w');
    
    $data = ["'1560254896878987878"];
    fputcsv($fp, $data);
    
    $data = ["15602548966666666666\t"];
    fputcsv($fp, $data)
    
    fclose($fp);
    
    echo "done";
```
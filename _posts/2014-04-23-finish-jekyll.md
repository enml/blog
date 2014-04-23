---
layout: post
title: "对5天来关于jekyll的心得"
description: ""
category: 技术分享
tags: [jekyll blog]
---
{% include JB/setup %}
# 完成基于jekyll的第一个blog
---

　今天差不多把blog完成了，这是我第一个基于jekyll的blog，定制了主题，修改了相关配置，以及解决了中文bug。现在把这5天的心得分享一下：

* 首先是中文问题，这个困扰我了很久，也花费了不少时间，不过最后总算找到解决办法。给我最大的感触就是，即使碰壁，也得硬着头皮找下去，如果放弃，那就前功尽弃了。

<!--break-->

* 然后是关于bootstrap，因为主题是基于bootstrap，所以这几天对bootstrap也有了深入的了解。Less预编译的思想其实挺方便的，只不过先前习惯了直接div+css的方式后一时难以习惯，但是，习惯是用来打破，不打破那永远都进不了步。

* @media通过检测min-width和max-width来进行响应式布局，但要编写全局css时要注意，否则很容易响应不了。

* \<hr> 添加个具有margin的hr，然后在使用card style时可以通过添加hr来达到分割的效果。另一种方式是直接为card添加一个margin-top。

* 当我使用中文的categories时，由于permalink中包含categories，导致链接失败。所以只要到_config.yml中修改permalink即可。
---
title:       "R语言ggpolot2气泡图展示棒球运动员的表现"
subtitle:    ""
description: ""
date:        2019-01-30
author:      ""
image:       ""
---

# R语言ggplot2气泡图展示棒球运动员的表现

2019年1月30号

数据来源链接 https://github.com/nanli-7/basketball_data_visualization


作图代码

```{r}
df<-read.csv("example_data/20190130/baseball_data.csv",
             header=T)
head(df)

library(dplyr)

df%>%
  group_by(handedness,height)%>%
  summarise(avg=mean(avg),n=n(),hr=mean(HR)) -> df1
head(df1)

library(ggplot2)

ggplot(df1,aes(x=height,y=avg))+
  geom_point(aes(fill=handedness,size=hr),
             alpha=0.5,shape=21)+
  scale_fill_manual(values = c("#fdc381","#99c1dc","#fc998e"))+
  scale_size_continuous(range=c(0,30))+
  scale_x_continuous(limits = c(65,80),
                     breaks = seq(65,80,1))+
  theme_bw()+
  theme(legend.position = "none")+
  ylim(0,0.4)+
  labs(x="A",y="B",title = "C",caption = "D")
```

欢迎大家关注我的公众号 

**小明的数据分析笔记本**

<img src="img/xiaoming.jpg">

> 公众号主要分享R语言ggplot2科研数据可视化的有趣实例
---
id: feature-vector-db
title: Feature vector database
sidebar_label: Feature vector database
---

# 特征向量数据库

既然特征向量检索是未来人工智能技术大规模应用的必要条件，那是否存在一个能高效存储检索特征向量的数据库呢？让我们先看看市场上目前关于特征向量检索有哪些具体实现。

## FAISS

FAISS是Facebook AI基于C++语言编写的一款开源、针对多媒体文件相似性搜索的算法库。FAISS支持开发人员对检索速度，内存使用和检索精度等的优化设置。但它仅仅是一个算法库，并且对开发人员有较高的使用要求。

## SPTAG

SPTAG是由Microsoft于2019年5月发布的，基于最近邻搜索的向量检索算法库。

SPTAG的优点是搜索速度快，毫秒内智能搜索数十亿条向量，并且在查询精确度和内存占用上表现佳。但缺点也很明显，其建图时间长，而且每此添加新向量进数据库，必须重新建图。                     

综上所述，当前工业界针对向量检索的实现中，并没有一个能擅长所有场景的万能算法。同时现有的实现也都还只是算法库，而并非一个系统。随着AI应用的大规模落地，提供一个面向海量特征向量检索的数据库系统，已经是市场对于数据库厂商提出的新需求。

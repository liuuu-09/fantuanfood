# fantuanfood
# fantuan
**项目简介**

饭团是仿照大众点评开发的一款美食点评项目，用户注册登录后根据商品类型、价格、店铺信息等多条件进行筛选店铺，在店铺详情页可以定位店铺的具体位置和收藏店铺。用户可以在饭团店铺中挑选美食以及参加秒杀低价抢购美食。在购买美食时用户可以在店铺内领取此店铺专享优惠券进行优惠减价。用户通过支付宝付款成功后可以查看到订单流水信息，也可以在个人中心查看订单的状态，包括已完成订单，待支付订单以及待评价订单。用户在筛选、浏览店铺时也可以对喜欢的店铺进行收藏，在个人中心中也可以查看。

**开发者**:张旭、商建、刘丽、刘海萍

**项目收获**

**软件架构说明**

该项目使用的框架时Spring Boot2.7.4

持久层由 Mybatis 逆向工程生成

数据库使用的是 MySQL 8.0.23

**使用的技术**

MybatisPlus、阿里云OSS存储、ElasticSearch 、IK分词器、Redis、thymeleaf、RSA、 AES、 sha2 短信注册、支付宝沙箱支付、RabbitMQ、RabbitMQ延时队列、死信队列

**系统要求**

JDK == 1.8

MySQL >= 5.8

Redis

ES

MySQL

#### 项目功能介绍

1. 注册登录
       使用RSA+AES+sha2+短信注册，全程保证保证用户的信息安全。

![image](https://user-images.githubusercontent.com/74643631/202430106-60246667-ccc1-4930-a598-5d2a86be5011.png)



2. 根据美食类型、价格多条件筛选店铺
       用户根据美食类型和价格范围多个条件筛选美食店铺。

![image](https://user-images.githubusercontent.com/74643631/202431042-45a3a510-8bf2-433f-a04f-65a8284e605d.png)



3. 根据店铺人均消费价格、店铺评分进行排序
       根据店铺的人均消费价格和店铺的评分对店铺进行排序。

![image](https://user-images.githubusercontent.com/74643631/202431192-88e5405a-fc04-4de6-a0da-f322655361bd.png)

4. 根据店铺信息搜索店铺
   根据店铺信息使用ElasticSearch进行查询；

![image](https://user-images.githubusercontent.com/74643631/202431481-81dee3e7-f424-43e2-814d-9d58f2323a71.png)

5. 收藏店铺
   当用户搜索浏览店铺时对感兴趣的店铺进行收藏，收藏后的店铺可在个人中心-我的收藏-收藏店铺中查看。
![image](https://user-images.githubusercontent.com/74643631/202431579-9484ddde-855c-49f5-945d-2429c56c80d1.png)



![image](https://user-images.githubusercontent.com/74643631/202431687-57abf1b4-9f84-4bc0-b3d7-2636e6d2fe23.png)

6. 查看店铺位置地图
       这里调用了高德地图的接口显示店铺的位置； 

![image](https://user-images.githubusercontent.com/74643631/202431949-ee079292-7b53-4cfd-b70e-3ac063bbcd27.png)
7.领取优惠券
          用户可以进入店铺，并领取当前店铺的优惠券，若优惠券超时未使用则失效。 

![image](https://user-images.githubusercontent.com/74643631/202432047-007d62dd-47ae-4dde-81d9-934ea9a1b35d.png)

![image](https://user-images.githubusercontent.com/74643631/202432108-74b60226-9303-4aa3-9d20-b8c8d2c047af.png)
![image](https://user-images.githubusercontent.com/74643631/202432163-611e0d6f-0600-421e-930d-3cb389fe3d76.png)

8. 商品秒杀
       使用redis完成秒杀功能，用户可参与每天固定时间段的秒杀活动进行低价抢购美食。

![image](https://user-images.githubusercontent.com/74643631/202432316-de160beb-773f-42ae-a1d6-ba4136438fb8.png)

9.使用优惠券
         在购买商品时选择使用优惠券进行价格减价。 
![image](https://user-images.githubusercontent.com/74643631/202432557-21f4d7ed-80b1-4985-8be6-16647d5a2ef4.png)

10.提交、生成订单、削峰限流、支付延时，自动取消
          购买且完成优惠券的选择后提交订单进行购买,在此处使用了RabbitMQ实现了订单削峰限流与支付延迟，当订单超时未支付时订单自动取消。

![image](https://user-images.githubusercontent.com/74643631/202432704-c05f418c-e063-4a7b-a59e-7050698ca33e.png)

11. 支付宝支付
           调用支付宝接口,使用支付宝沙箱进行支付生成流水。

![image](https://user-images.githubusercontent.com/74643631/202432920-aca4cf56-8eeb-4b77-aaad-e589f8394a33.png)

![image](https://user-images.githubusercontent.com/74643631/202432992-c1fbda92-640b-4b90-9879-085048f7ba5f.png)


![image](https://user-images.githubusercontent.com/74643631/202433091-cd451f5f-e97c-40a7-b28e-183e5eecb99b.png)

12. 评论订单
          完成支付后生成订单，在个人中心查看订单去进行订单评价。

![image](https://user-images.githubusercontent.com/74643631/202433205-7cab803d-35e3-445b-a466-bd33b974c6b3.png)

![image](https://user-images.githubusercontent.com/74643631/202433262-dc94b29e-5131-402f-879a-d2155f313e39.png)

13. 个人中心
          用户登录成功后可在个人中心查看订单、优惠券、收藏、个人信息功能。具体包括订单的全部订单，待评论订单、未付款订单。优惠券包括已领取的优惠券、失效的优惠券。收藏的店铺和用户个人信息。
![image](https://user-images.githubusercontent.com/74643631/202433352-c6595734-3da7-47fe-a413-77d81decc21f.png)

![image](https://user-images.githubusercontent.com/74643631/202433441-9d325d6d-6f25-4cdf-a456-aad65064ad49.png)

![image](https://user-images.githubusercontent.com/74643631/202433500-81df53f8-4df0-4347-8531-5455a37fd10b.png)












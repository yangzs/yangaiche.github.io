<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [api](#api)
  - [有的没的](#有的没的)
    - [接口权限](#接口权限)
    - [接口版本管理](#接口版本管理)
    - [错误返回格式](#错误返回格式)
    - [所有信息组织结构](#所有信息组织结构)
- [公共数据](#公共数据)
  - [车辆例表](#车辆例表)
    - [获取](#获取)
    - [过滤](#过滤)
    - [增改](#增改)
    - [删除](#删除)
  - [支付](#支付)
  - [订单](#订单)
  - [评价](#评价)
  - [车](#车)
  - [优惠券](#优惠券)
  - [优惠码](#优惠码)
  - [手机验证码](#手机验证码)
  - [加入购物车](#加入购物车)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# api
## 有的没的
### 接口权限

在报头 API-Access-Token中

### 接口版本管理

在链接中指定
http://192.168.1.1:8000/***v1***/api/xxx

### 错误返回格式
```json
{

    "error_msg": "An active access token must be used to query information about the current user.", 
    "error_type": "OAuthException", 
    "error_code": 2500 //由服务器定义
 
}
```
### 所有信息组织结构
```json
{
"user_info":
{
	"basic":
	{
		"id":1233333,
		"phone_number":"15010111335",
		"name":"刘正青",
		"gender":"male",
		"avatar_img":"http://www.baidu.com/a.png",
	},
	"location":
	[
	    {
	    "id":1,
		"latitude":12333.1231231,
		"longtitude":1231231.1232,
		"province_name":"湖南",
		"city_name":"长沙",
		"district_name":"雨花区",
		"stree_name":"芙蓉东路",
		"location_name":"国际大厦"
		},
	],
	"cars":
	[
		{
			"id":1,
			"licence":
			{
				"province":"京",
				"number":"RB0718"
			},
			"bought_time":"2011-08-21T18:02:52.249Z", 
			"miles":12333,
			"chassis_numher":"HIBIY797DFS77",
			"engine_number":"DFUSODFND567DFSDN-SDFC",
			"brand":"大众",
			"category":"途观",
			"model":"豪华版 2.0T",
			"brand_img_url":"http://www.baidu.com/a.png",

			"scores":
			{
				"whole_score":78,
				"parts":[
				{
					"name":"轮胎",
					"status":"需更换",
					"used_hours":123,
					"usrd_miles":123,
					"score":80,
					"comment":"破损严重,建议更换",
				}
				]
			},

		}
	],
	"coupons":
	[
		{
			"id":1,
			"status":"已用",
			"number":"37123322",
			"value":99.00,
			"expired_time":"2011-08-21T18:02:52.249Z",
		}
	],
"check_reports":
[
	{
		"id":1,
		"name":"报告单",
		"complete_time":"2011-08-21T18:02:52.249Z",
		"car":{
			"car_id":1,
			"licence":
			{
				"province":"京",
				"number":"RB0718"
			},
			"bought_time":"2011-08-21T18:02:52.249Z",
			"miles":12333,
			"chassis_numher":"HIBIY797DFS77",
			"engine_number":"DFUSODFND567DFSDN-SDFC",
			"brand":"大众",
			"category":"途观",
			"mode":"豪华版 2.0T",
			"brand_img_url":"http://www.baidu.com/a.png",
		},
		"reports":
		[
			{
				"name":"电瓶电压及寿命检测",
				"status":"合格",//已修复//未修复
				"stars":4,
				"status_comment":"华晨宝马行驶20000公里后电瓶XXXX,经检测发现要爆炸,需要及时更换",
				"imgs":
				[
					"http://www.baidu.com/a.png",
				]
			},
		]
	}
]
},
"order_infos":[
{
	"id":1,
	"name":"常规保养",
	"status":"初检中",
	"keeper_name":"张师傅",
	"_place_time":"2011-08-21T18:02:52.249Z", //  下单时间
	"start_time":"2011-08-21T18:02:52.249Z",  // 接单时间
	"order_services":[
		{
			"id":12,
			"type":"保养",
			"name":"机滤通用",
			"unit":"升",
			"unit_count":1,
			"price":123.00,
		}
	],
	"order_flow":[
		{
			"id" : 1,
			"name":"接车",
			"status":"已完成",
			"complete_time":"2011-08-21T18:02:52.249Z",
			"location":"中关村南大街",
			"imgs":[
			"http://www.baidu.com/a.png",
			"http://www.baidu.com/b.png",
			]
		},
		{
			"id" : 2,
			"name":"保养",
			"status":"未完成",
		}
	],
	"client_feedback":
	{
		"comment":"非常不错,下次再来!",
		"keeper_stars":4,
		"order_stars":5,
	}

}
],
"carcare_book":[
{
	"car_id":1,
	"history":[
		{
			"miles":10000,
			"events":[
			{
				"name":"检测机滤",
				"status":"未完成",//完成,
			}
			]
		}
	]
}
],

}
```
#公共数据
## 车辆例表
###  获取
```json
GET /api/brands
{
		"brands":
		[
			{
			"id":1,
			 "name":"大众",
			 "img_url":"http://www.baidu.com/a.png",
			 "categories":
			 [
			 	{
			 	"brand_name":"大众",
			 	"name":"途观",
			 	"modoles":[
					 "豪华版 2.0T",
					 "豪华版 3.0T"
			 	],
			 	}
			 ],
			 }
		],

}
```
### 过滤
```json
GET /api/brands?name="大众"
{
"id":1,
 "name":"大众",
 "img_url":"http://www.baidu.com/a.png",
 "categories":
 [
 	{
 	"brand_name":"大众",
 	"name":"途观",
 	"modoles":[
		 "豪华版 2.0T",
		 "豪华版 3.0T"
 	],
 	}
 ],
}

```

### 增改
```json
POST /api/brands
BODY
{
 "brand_name":"大众",
 "categorie_name":"途观",
 "modole_name":"豪华版 3.0T",
 "img_base64":"sklfjsfsdon",
}

```

### 删除
```json
DELETE  /api/brands/{id}
DELETE  /api/brands/{id}/categories/{id}
DELETE  /api/brands/{id}/categories/{id}/modoles/{id}
```

## 支付
```json

POST  /api/payment/{id}
{

}

```


## 订单

## 评价

## 车

## 优惠券

## 优惠码

## 手机验证码
```json
GET  api/phone_verify/15010111335
```
## 加入购物车
```json
POST  api/cart/
{
	"name":"常规保养",
	 "car_id",1,
	 "contact_name":"王语嫣",
	 "contact_phone_number":"15010111335",
	 "use_coupon_id":[1,3],
	 "serivces":[
	 	{
	 		"type":"机油",
	 	},
	 	{
	 		"type":"机滤",
	 	}
	 ]
	 "comment":"要两瓶",
	 "pick_time_segment":[
	 	"2011-08-21T18:02:52.249Z",
	 	"2011-08-21T18:03:52.249Z"
	 ],
	 "location":{
		"latitude":12333.1231231,
		"longtitude":1231231.1232,
		"province_name":"湖南",
		"city_name":"长沙",
		"district_name":"雨花区",
		"stree_name":"芙蓉东路",
		"location_name":"国际大厦"
		},
	"order_services":[
		{
			"id":12,
			"type":"保养",
			"name":"机滤通用",
			"unit":"升",
			"unit_count":1,
			"price":123.00,
		}
	],
}

```

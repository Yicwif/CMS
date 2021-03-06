# CMS
hackson: CMS product by team CYC.

### (1)[POST] /content_types/:content_type_id

说明

	【管理员】发布一个content_type

输入参数说明：
	
	name: 名称
	description: 描述

输入样例：

	POST /content_types/car_info HTTP/1.1 
	Accept: application/json

	{
		"name": "汽车信息",
		"description": "汽车的型号、动力、配置等参数"
	}


### (2)[PUT] /content_types/:content_type_id

说明

	【管理员】更新一个content_type

输入参数说明：
	
	name: 字段的名称
	id: 字段的id （同一content_type_id下的字段id唯一）
	type: 字段的描述

输入样例：

	PUT /content_types/car_info HTTP/1.1 
	Accept: application/json

	{
	  "fieldscount": 3,
	  "fields":[
	      {
	         "name": "型号",
	         "id": "model",
	         "type": "string"
	      },
	      {
	         "name": "变速器",
	         "id": "transmission",
	         "type": "string"
	      },
	      {
	         "name": "排量",
	         "id": "displacement",
	         "type": "string"
	      }
	  ]
	}


### (3)[GET] /content_types

说明

	【用户】获取所有content_types信息

输入参数说明：
	
  无

输入样例：

	GET /content_types HTTP/1.1 
	Accept: application/json

输出样例：
        
	{
		"total": 2,
		"results": [
		  {
	             "name": "汽车信息",
	    	     "id": car_info,
	    	     "description": "汽车的型号、动力、配置等参数",
	    	     "updatetime": "2016-09-08 19:00:19"
   	         },
   	         {
   	             "name": "房产信息",
	             "id": "house_info",
                     "description": "各城市的楼市信息",
	    	     "updatetime": "2016-09-08 19:02:13"
   	         }
		]
	}
	

### (4)[GET] /content_types/:content_type_id

说明

	【用户】获取指定content_type_id的信息

输入参数说明：
	
  无

输入样例：

	GET /content_types/car_info HTTP/1.1 
	Accept: application/json

输出样例：
        
	{
	  "name":  "汽车信息",
	  "id": car_info,
	  "description": "汽车的型号、动力、配置等参数",
	  "updatetime": "2016-09-08 19:00:19",
	  "fieldscount": 3,
	  "fields":[
	      {
	         "name": "型号",
	         "id": "model",
		 "type":"string"
	      },
	      {
	         "name": "变速器",
	         "id": "transmission",
		 "type":"string"
	      },
	      {
	         "name": "排量",
	         "id": "displacement",
          	 "type":"string"
	      }
	  ]
	}
	

### (5)[POST] /contents/:content_id

说明

	【管理员】发布一条content

输入参数说明：
	
	content_id: 唯一id
	content_type_id: 所属content_type,必填
	name: 名称
	description: 描述
	fieldsvalue: 各字段的名称和值. 需要先查询出此content_type的各个字段名称

输入样例：

	POST /contents/BenChiC200L HTTP/1.1 
	Accept: application/json

	{
		"name": "奔驰C200L信息",
		"description": "2016款奔驰C200L",
		"content_type_id": "car_info",
		"fieldsvalue":[
		  { 
		     "id":"model",
		     "name":"型号",
		     "value":"奔驰C200L",
		     "type":"string"
		  },
		  { 
		     "id":"transmission",
		     "name": "变速器",
		     "value":"自动挡",
		     "type":"string"
		  }
		  { 
		     "id":"displacement",
		     "name": "排量",
		     "value":"2.0L",
		     "type":"string"
		  }
		]
	}


### (6)[GET] /contents/:content_id

说明

	【用户】获取一条content

输入参数说明：
	
	content_type_id: 所属content_type
	name: 名称
	description: 描述
	updatetime: 最后更新时间
	createuser: 创建者
	fieldsvalue: 各字段的名称和值. 需要先查询出此content_type的各个字段名称

输入样例：

	GET /contents/BenChiC200L HTTP/1.1 
	Accept: application/json

	{
		"name": "奔驰C200L信息",
		"content_type_id": "car_info",
		"description": "2016款奔驰C200L",
		"updatetime": "2016-09-05 18:39:03",
		"createuser": "ywm@asiainfo.com",
		"fieldsvalue":[
		  {
		     "id":"model",
		     "name": "变速器",
		     "value":"奔驰C200L",
		     "type":"string"
		  },
		  { 
		     "id":"transmission",
		     "name": "变速器",
		     "value":"自动挡",
		     "type":"string"
		  }
		  { 
		     "id":"displacement",
		     "name": "排量",
		     "value":"2.0L",
		     "type":"string"
		  }
		]
	}
	
	
### (7)[GET] /contents

说明

	【用户】获取所有content

输入参数说明：
	
	无

输出样例：

	GET /contents HTTP/1.1 
	Accept: application/json

	{
		"total": 3,
		"results": [
		{
		   "content_id": "BenChiC200L",
	           "name": "奔驰C200L信息",
		   "content_type_id": "car_info"
		},
   	         {
   	             "content_id": "LAND_ROVER",
		     "name": "路虎揽胜",
		     "content_type_id": "car_info"
   	         }
		]
	}

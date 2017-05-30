## 百度地图web服务

###[Place API](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-placeapi) 是一类简单的接口，用于返回查询某个区域的某类POI数据，且提供单个POI的详情查询服务，用户可以使用C#、C++、Java等开发语言发送请求且接收json、xml的数据。

```
// search
caller := bdm.BaiduApi{"your ak", "v2"}
params := make(map[string]string)
params["query"] = "美食"
params["page_size"] = "10"
params["page_num"] = "0"
params["scope"] = "1"
params["bounds"] = "39.915,116.404,39.975,116.414"
ret, err := caller.PlaceSearch(params)
fmt.Println(ret.(*bdm.PlaceSearchRet), err)
//detail
caller := bdm.BaiduApi{"your ak", "v2"}
params := make(map[string]string)
params["uid"] = "5a8fb739999a70a54207c130"
params["scope"] = "2"
ret, err := caller.PlaceDetail(params)
fmt.Println(ret.(*bdm.PlaceDetailRet), err)
```

###[Place Suggestion API](http://lbsyun.baidu.com/index.php?title=webapi/place-suggestion-api) Place suggestion API 是一套提供匹配用户输入关键字辅助信息、提示服务的接口，可返回json或xml格式的一组建议词条的数据。
```
caller := bdm.BaiduApi{"your ak", "v2"}
params := make(map[string]string)
params["query"] = "天安门"
params["region"] = "北京市"
params["city_limit"] = "true"
ret, err := caller.Suggestion(params)
fmt.Println(ret.(*bdm.SuggestionRet), err)

```

###[Geocoding API](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-geocoding) Geocoding API 是一类接口，用于提供从地址到经纬度坐标或者从经纬度坐标到地址的转换服务，用户可以使用C# 、C++、Java等开发语言发送请求且接收JSON、XML的返回数据。
```
// 从地址到经纬度坐标
caller := bdm.BaiduApi{"your ak", "v2"}
params := make(map[string]string)
params["address"] = "北京市海淀区上地十街10号"
// params["pois"] = "1"
ret, err := caller.Geocoding(params)
fmt.Println(ret.(*bdm.GeoEncoderRet), err)
// 经纬度坐标到地址
caller := bdm.BaiduApi{"your ak", "v2"}
params := make(map[string]string)
params["location"] = "39.983424,116.322987"
params["pois"] = "1"
caller.Geocoding(params)
```

###[坐标转换API](http://lbsyun.baidu.com/index.php?title=webapi/guide/changeposition) 百度地图坐标转换API是一套以HTTP形式提供的坐标转换接口，用于将常用的非百度坐标（目前支持GPS设备获取的坐标、google地图坐标、soso地图坐标、amap地图坐标、mapbar地图坐标）转换成百度地图中使用的坐标，并可将转化后的坐标在百度地图JavaScript API、车联网API、静态图API、web服务API等产品中使用
```
caller := bdm.BaiduApi{"your ak", "v2"}
params := make(map[string]string)
params["location"] = "39.983424,116.322987"
params["pois"] = "1"
caller.Geocoding(params)
```
定义了如下常量方便使用

```
GEOCONV_F_WGS84  = "1"
GEOCONV_F_SOGOU  = "2"
GEOCONV_F_GOOGLE = "3"
GEOCONV_F_SOSO   = "3"
GEOCONV_F_ALIYUN = "3"
GEOCONV_F_MAPABC = "3"
GEOCONV_F_MET    = "4"
GEOCONV_F_BD_LL  = "5"
GEOCONV_F_BD_MET = "6"
GEOCONV_F_MAPBAR = "7"
GEOCONV_F_51     = "8"
GEOCONV_T_BD09ll = "5"
GEOCONV_T_BD09MC = "6"
```
-
<h1 align="center"> my-weather </h1>

<p align="center">这是个学习demo.</p>


## 安装

```shell
$ composer require mazha/my-weather 0.0.1
```

## 使用

##### demo 1.
```
use  Mazha\MyWeather\Weather;
$key = 'xxxxxxxxxxxxxxxxxxxxxxxxxxx';
$weather = new Weather($key);
```
#### ***获取实时天气***
```

$response = $weather->getWeather('深圳');
```
###### **返回示例:**
```$xslt
{
    "status": "1",
    "count": "1",
    "info": "OK",
    "infocode": "10000",
    "lives": [
        {
            "province": "广东",
            "city": "深圳市",
            "adcode": "440300",
            "weather": "中雨",
            "temperature": "27",
            "winddirection": "西南",
            "windpower": "5",
            "humidity": "94",
            "reporttime": "2018-08-21 16:00:00"
        }
    ]
}
```
#### ***返回近期天气***

```$xslt
$response = $weather->getWeather('深圳', 'all');
```
###### **返回示例:**
```$xslt
{
    "status": "1", 
    "count": "1", 
    "info": "OK", 
    "infocode": "10000", 
    "forecasts": [
        {
            "city": "深圳市", 
            "adcode": "440300", 
            "province": "广东", 
            "reporttime": "2018-08-21 11:00:00", 
            "casts": [
                {
                    "date": "2018-08-21", 
                    "week": "2", 
                    "dayweather": "雷阵雨", 
                    "nightweather": "雷阵雨", 
                    "daytemp": "31", 
                    "nighttemp": "26", 
                    "daywind": "无风向", 
                    "nightwind": "无风向", 
                    "daypower": "≤3", 
                    "nightpower": "≤3"
                }, 
                {
                    "date": "2018-08-22", 
                    "week": "3", 
                    "dayweather": "雷阵雨", 
                    "nightweather": "雷阵雨", 
                    "daytemp": "32", 
                    "nighttemp": "27", 
                    "daywind": "无风向", 
                    "nightwind": "无风向", 
                    "daypower": "≤3", 
                    "nightpower": "≤3"
                }, 
                {
                    "date": "2018-08-23", 
                    "week": "4", 
                    "dayweather": "雷阵雨", 
                    "nightweather": "雷阵雨", 
                    "daytemp": "32", 
                    "nighttemp": "26", 
                    "daywind": "无风向", 
                    "nightwind": "无风向", 
                    "daypower": "≤3", 
                    "nightpower": "≤3"
                }, 
                {
                    "date": "2018-08-24", 
                    "week": "5", 
                    "dayweather": "雷阵雨", 
                    "nightweather": "雷阵雨", 
                    "daytemp": "31", 
                    "nighttemp": "26", 
                    "daywind": "无风向", 
                    "nightwind": "无风向", 
                    "daypower": "≤3", 
                    "nightpower": "≤3"
                }
            ]
        }
    ]
}
```
#### ***返回xml格式数据***
######默认返回是json格式，第三个参数设定返回数据格式
```$xslt
$response = $weather->getWeather('深圳', 'all', 'xml');
```
###### **返回示例:**
```$xslt

<response>
    <status>1</status>
    <count>1</count>
    <info>OK</info>
    <infocode>10000</infocode>
    <lives type="list">
        <live>
            <province>广东</province>
            <city>深圳市</city>
            <adcode>440300</adcode>
            <weather>中雨</weather>
            <temperature>27</temperature>
            <winddirection>西南</winddirection>
            <windpower>5</windpower>
            <humidity>94</humidity>
            <reporttime>2018-08-21 16:00:00</reporttime>
        </live>
    </lives>
</response>
```

### 调用参数说明

```$xslt
array|string getWeather(string $city, string $type = 'base', string $format = 'json')
```
 * $city - 城市名，比如：“深圳”；
 * $type - 返回内容类型：base: 返回实况天气 / all: 返回预报天气；
 * $format - 输出的数据格式，默认为 json 格式，当 output 设置为 “xml” 时，输出的为 XML 格式的数据。

### laravel 中使用
###### ***修改config/services.php***
```
 'weather' => [
        'key' => env('WEATHER_API_KEY'),
    ]
```
##### ***添加env配置***
```
WEATHER_API_KEY=xxxx
```
##### demo.
```
$response = app('weather')->getWeather('深圳')
```

## 贡献

你可以通过三种途径联系到作者:

1. 提交地址 [issue tracker](https://github.com/MAZHAL/my-weather/issues).
2. 回答问题或者bug修复 [issue tracker](https://github.com/MAZHAL/my-weather/issues).
3. 提供新功能或者wiki.

_代码贡献过程不是很正式。您只需要确保遵循PSR-0、PSR-1和PSR-2编码准则。在适用的情况下，任何新的代码贡献都必须伴随着单元测试。_

## License

MIT
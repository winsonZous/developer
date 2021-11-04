## JSON

### 背景：目前主流的前后端分离的架构。JSON用于前后端数据传输。java中并没有JSON的解析工具类，编码与解码JSON需要借助第三方类库。 下面是几个常用的 JSON 解析类库：
### 本质： Java对象 字符串 JSON对象 三者相互转换
- Gson: 谷歌的 JSON ，功能十分全面。
- FastJson: 阿里巴巴大神高铁开发的 JSON 库，性能十分优秀，漏洞也很多。
- Jackson: 社区十分活跃且更新速度很快。

```
    <dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.74</version>
    </dependency>
```

## 编码

```
@Test
    public void encodeJson() {
        JSONObject json = new JSONObject();
        // int
        json.put("int", 1);
        // string
        json.put("string", "string");
        // boolean
        json.put("boolean", true);
        // array
        List<Integer> integers = Arrays.asList(2, 1, 3, 5, 4, 4, 3);
        json.put("list", integers);
        // null
        json.put("null", null);
        System.out.println(json);
    }
    /** 结果
     * {"boolean":true,"string":"string","list":[2,1,3,5,4,4,3],"int":1}
     * */
```

## 解码

```
    @Test
    public void decodeJson() {
        JSONObject json = JSONObject
                .parseObject("{\"boolean\":true,\"string\":\"string\",\"list\":[2,1,3,5,4,4,3],\"int\":1}");
        // int
        int i = json.getIntValue("int");
        System.out.println(i);
        // string
        String s = json.getString("string");
        System.out.println(s);
        // boolean
        boolean b = json.getBooleanValue("boolean");
        System.out.println(b);
        // list
        List<Integer> integers = JSON.parseArray(json.getJSONArray("list").toJSONString(), Integer.class);
        integers.forEach(System.out::println);
        // null
        System.out.println(json.getString("null"));
    }
    /** 结果
     * string
     * true
     * 2
     * 1
     * 3
     * 5
     * 4
     * 4
     * 3
     * null
     */
```

## 具体使用

- JSONObject = JSON.parseObject() 字符串->JSON对象
- JSON.parseArray()    从字符串解析 JSON 数组
- JSON.toJSONString(obj/array)    将 JSON 对象或 JSON 数组转化为字符串
- JSONObject本质是个Map，JSONArray本质是个List，所以没有必要进行JSONObject与Map，JSONArray与List之间的转换
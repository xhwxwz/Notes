# Shell脚本将字符串转换为标准json

## 问题

开发过程中，发现上传到hdfs的json文件下载下来都是字符串格式，假设文件名为person.json，示例如下

```
"{  \\"person\\": [{\\"name\\":  \\"david\\",  \\"age\\":  \\"25\\"}]}"
```

而在java代码中需要读取的是标准json格式的文件，示例如下：

```json
{
    "person":[
        {
            "name":  "david",
            "age":  "25"
        }
    ]
}
```



## 解决办法

```shell
# \" replace to "
sed -i 's#\\"#"#g'  person.json

# \n replcace to wrap display
echo -e "$(cat person.json)" > person.json

#delete the first two lines
sed -i 'ld' person.json
sed -i 'ld' person.json

#delete the last two lines
sed -i '$d' person.json
sed -i '$d' person.json

#add { before the first line
sed -i 'li {' person.json

#add } after the end line
sed -i '$a }' person.json

```


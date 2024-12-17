# 说明页面入口

[说明页面入口](https://cloudforceiot.github.io/ExtendedProductsExample/)

# 例子 总入口 modules-app-extra

如:

https://cloudforceiot.github.io/ExtendedProductsExample/modules-app-extra.json

```json
{
  "product-profiles": [
    "https://api-cdn.ubibot.cn/configs/product-profiles/all"
  ],
  "extended-modules": [
    "https://api-cdn.ubibot.cn/configs/extended-modules"
  ],
  "extended-products": [
    "https://app-ext.ubibot.cn/extended-products/all.json"
  ]
}
```

product-profiles 对应传统的 https://api-cdn.ubibot.cn/configs/product-profiles/all

extended-modules 对应 extended-modules.json

extended-products/all.json (因为实际部署会以extended-products作为目录，all.json作为文件名，该目录下含有不同型号的子目录)对应 extended-products.json


# 数据入口

[数据入口](https://cloudforceiot.github.io/ExtendedProductsExample/extended-products.json)

# 服务器入口

configs/extended-products

例如: https://api-cdn.ubibot.cn/configs/extended-products/all

建议的目录结构是

```
configs
 |
 +-- extended-products
   |
   +-- all (即extendedProducts.json文件的内容)
   |
   +-- test001 (产品目录，如产品图片，多国文件)
     |
     +-- localized.json
     +-- xxx.png
     +-- xxx.gif
     +-- 其它资源文件...
   |   
   +-- 其它产品资源目录...
```
     
# 多国格式

使用simplelocalized.io的multi language json模式

# 注意事项

1. iOS不支持svg格式，需要转换为png

2. productId保证不要与内置的重复，理论上优先走内置的，但可能存在不可预测的行为

3. productId在定义文件中必须唯一，否则会进行除重处理，完全排除这个productId

4. productId不要使用ubibot-extest，app内置测试用

5. families可以多个，需要保证是兼容的，否则也可能存在不可预测的行为，例如同时为sp1和aqs1时，概况页根据代码的判定顺序显示第一类

6. 图片必须压缩（特别需要注意gif的大小），否则会对加载性能造成影响，目前是顺序序列式预载

7. 如果product非内置，也不是这里定义的，则走旧有的预发布流程页面

8. 多国可以复用同一条，减少平台额度的重复占用

9. 多国的fallback处理默认为en，即如果找不到对应语言的key，则会使用en，如果en也没有，则直接显示key

10. 多国key取值，除中文会使用secondary部分外，其余只取primary，例如 zh，zh_Hant，en, pt, ...

11. 资源目录不支持 相对 或 绝对 路径，以配置文件的所在目录为base


## 其它说明

README.md, index.html不需要放到服务器

## 附录

### 内置的families (不区分大小写，但尽量使用小写以免不测)

目前影响概况页的显示模式 以及 是否归类为channel还是gateway（两者互斥，也即使channels不会显示gateways的内容，反之亦然）

如果自定义新的family，目前理论上不构成实质影响，但命名尽量按以下的模式

```
ws1
ws1a
gs1a
gs2a
ws1pb
ws1p
gs1
gs2
ld1
nr1
gw1
cb1
sp1
ms1
ms1p
aqs1
```

### 目前支持的多国keys

```
zh          
zh_Hant     中文繁体
en          
ja
pl          Polish
fr          French
es          Spanish
ru          Russian
pt          Portuguese
nl          Dutch
kr          
it          Italian
vi          Vietnamese
de          German
ar          Arabic
```





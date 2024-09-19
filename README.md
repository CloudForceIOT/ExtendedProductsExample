# 说明页面入口

[说明页面入口](https://cloudforceiot.github.io/ExtendedProductsExample/)


# 数据入口

[数据入口](https://cloudforceiot.github.io/ExtendedProductsExample/extendedProducts.json)


# 多国格式

使用simplelocalized.io的multi language json模式

# 注意事项

1. iOS不支持svg格式，需要转换为png

2. productId保证不要与内置的重复，理论上优先走内置的，但可能存在不可预测的行为

3. families可以多个，需要保证是兼容的，否则也可能存在不可预测的行为，例如同时为sp1和aqs1时，概况页根据代码的判定顺序显示第一类

4. 多国可以复用同一条，减少平台额度的重复占用

5. 图片必须压缩（特别需要注意gif的大小），否则会对加载性能造成影响，目前是顺序序列式预载


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


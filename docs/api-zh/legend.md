<!--## _geom_.legend() 配置图例-->

`markdown:common/style.md`

<div class='custom-api-docs'>

配置图例有两种方式

第一种，传入 `boolean` 设置是否显示图例。

```ts
chart.legend(false); // 关闭图例
```

第二种，传入 _LegendCfg_ 对图例进行整体配置。

```ts
// highlight-start
(field: legendOption) => View;
// highlight-end

chart.legend({
  position: 'right',
});
```

第三种，对 field 字段对应的图例进行配置。

```ts
// highlight-start
(field: string, legendOption) => View;
// highlight-end

// 关闭某个图例，通过数据字段名进行关联
view.legend('city', false);

// 对特定的图例进行配置
view.legend('city', {
  position: 'right',
});
```

_LegendCfg_ 配置如下：

有的配置项作用范围区分分类图例和连续图例：
<tag color="green" text="分类图例">分类图例</tag>
<tag color="cyan" text="连续图例">连续图例</tag>

### LegendCfg.layout

<description> _'horizontal' | 'vertical'_ **optional** </description>

布局方式： horizontal，vertical

### LegendCfg.position

<description> _"top" | "top-left" | "top-right" | "right" | "right-top" | "right-bottom" | "left" | "left-top" | "left-bottom" | "bottom" | "bottom-left" | "bottom-right"_ **optional** </description>

图例的位置。

### LegendCfg.background

<description> _LegendBackgroundCfg_ **optional** </description>

背景框配置项。_LegendBackgroundCfg_ 配置如下：

| 参数名  | 类型                | 是否必选 | 默认值 | 描述           |
| ------- | ------------------- | -------- | ------ | -------------- |
| padding | number \| number[]  |          | -      | 背景的留白     |
| style   | [ShapeAttrs](shape) |          | -      | 背景样式配置项 |

### LegendCfg.flipPage

<description> _boolean_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，当图例项过多时是否进行分页。

### LegendCfg.handler

<description> _ContinueLegendHandlerCfg_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，滑块的配置项。_ContinueLegendHandlerCfg_ 配置如下：

| 参数名 | 类型                | 是否必选 | 默认值 | 描述           |
| ------ | ------------------- | -------- | ------ | -------------- |
| size   | number              |          | -      | 滑块的大小     |
| style  | [ShapeAttrs](shape) |          | -      | 滑块的样式设置 |

### LegendCfg.itemHeight

<description> _number_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例的高度，默认为 null。

### LegendCfg.itemWidth

<description> _number_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例项的宽度, 默认为 null，自动计算。

### LegendCfg.itemName

<description> _LegendItemNameCfg_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例项 name 文本的配置。_LegendItemNameCfg_ 配置如下：

| 参数名    | 类型                                                    | 是否必选 | 默认值 | 描述                             |
| --------- | ------------------------------------------------------- | -------- | ------ | -------------------------------- |
| style     | [ShapeAttrs](shape)                                     |          | -      | 文本样式配置项                   |
| spacing   | number                                                  |          | -      | 图例项 marker 同后面 name 的间距 |
| formatter | `(text: string, item: ListItem, index: number) => any;` |          |        | 格式化函数                       |

### LegendCfg.itemSpacing

<description> _number_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，控制图例项水平方向的间距。

### LegendCfg.itemValue

<description> _LegendItemValueCfg_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例项 value 附加值的配置项。_LegendItemValueCfg_ 配置如下：

| 参数名     | 类型                                                    | 是否必选 | 默认值  | 描述                                               |
| ---------- | ------------------------------------------------------- | -------- | ------- | -------------------------------------------------- |
| style      | [ShapeAttrs](shape)                                     |          | -       | 文本样式配置项                                     |
| alignRight | boolean                                                 |          | `false` | 是否右对齐，默认为 false，仅当设置图例项宽度时生效 |
| formatter  | `(text: string, item: ListItem, index: number) => any;` |          |         | 格式化函数                                         |

### LegendCfg.animate

<description> _boolean_ **optional** _default:_ `true` </description>

是否开启动画开关。

### LegendCfg.animateOption

<description> _ComponentAnimateOption_ **optional** </description>

动画参数配置，当且仅当 animate 属性为 true，即动画开启时生效。动画配置详情点击 [ComponentAnimateOption](animate-option) 查看。

### LegendCfg.label

<description> _ContinueLegendLabelCfg_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，文本的配置项。_ContinueLegendLabelCfg_ 配置如下：

| 参数名  | 类型                | 是否必选 | 默认值 | 描述                                                                                                                                          |
| ------- | ------------------- | -------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| align   | string              |          | -      | 文本同滑轨的对齐方式 <br/> - rail ： 同滑轨对齐，在滑轨的两端 <br/> - top, bottom: 图例水平布局时有效 <br/> - left, right: 图例垂直布局时有效 |
| style   | [ShapeAttrs](shape) |          | -      | 文本样式配置项                                                                                                                                |
| spacing | number              |          | -      | 文本同滑轨的距离                                                                                                                              |

### LegendCfg.marker

<description> _MarkerCfg_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例项的 marker 图标的配置。

`markdown:common/marker-cfg.md`

### LegendCfg.min

<description> _number_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，选择范围的最小值。

### LegendCfg.max

<description> _number_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，选择范围的最大值。

### LegendCfg.maxWidth

<description> _number_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例项最大宽度设置。

### LegendCfg.maxHeight

<description> _number_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例项最大高度设置。

### LegendCfg.offsetX

<description> _number_ **optional** </description>

图例 x 方向的偏移。

### LegendCfg.offsetY

<description> _number_ **optional** </description>

图例 y 方向的偏移。

### LegendCfg.rail

<description> _ContinueLegendRailCfg_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，图例滑轨（背景）的样式配置项。_ContinueLegendRailCfg_ 配置如下：

| 参数名        | 类型                | 是否必选 | 默认值 | 描述                                                                             |
| ------------- | ------------------- | -------- | ------ | -------------------------------------------------------------------------------- |
| type          | string              |          | -      | rail 的类型，color, size                                                         |
| size          | number              |          | -      | 滑轨的宽度                                                                       |
| defaultLength | number              |          | -      | 滑轨的默认长度，，当限制了 maxWidth,maxHeight 时，不会使用这个属性会自动计算长度 |
| style         | [ShapeAttrs](shape) |          | -      | 滑轨的样式                                                                       |

### LegendCfg.reversed

<description> _boolean_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，是否将图例项逆序展示。

### LegendCfg.slidable

<description> _boolean_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，滑块是否可以滑动。

### LegendCfg.title

<description> _G2LegendTitleCfg_ **optional** </description>

图例标题配置，默认不展示。_G2LegendTitleCfg_ 配置如下：

| 参数名  | 类型                | 是否必选 | 默认值 | 描述               |
| ------- | ------------------- | -------- | ------ | ------------------ |
| spacing | number              |          | -      | 标题同图例项的间距 |
| style   | [ShapeAttrs](shape) |          | -      | 文本样式配置项     |

### LegendCfg.track

<description> _ContinueLegendTrackCfg_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，选择范围的色块样式配置项。_ContinueLegendTrackCfg_ 配置如下：

| 参数名 | 类型                | 是否必选 | 默认值 | 描述           |
| ------ | ------------------- | -------- | ------ | -------------- |
| style  | [ShapeAttrs](shape) |          | -      | 选定范围的样式 |

### LegendCfg.values

<description> _number[]_ **optional** </description>

适用于 <tag color="cyan" text="连续图例">连续图例</tag>，选择的值。

### LegendCfg.custom

<description> _boolean_ **optional** </description>

是否为自定义图例，当该属性为 true 时，需要声明 items 属性。

### LegendCfg.items

<description> _LegendItem[]_ **optional** </description>

适用于 <tag color="green" text="分类图例">分类图例</tag>，用户自己配置图例项的内容。_LegendItem_ 配置如下：

| 参数名 | 类型        | 是否必选 | 默认值 | 描述                     |
| ------ | ----------- | -------- | ------ | ------------------------ |
| id     | string      |          | -      | 唯一值，用于动画或者查找 |
| name   | string      | required | -      | 名称                     |
| value  | any         | required | -      | 值                       |
| marker | _MarkerCfg_ |          | -      | 图形标记                 |

`markdown:common/marker-cfg.md`

</div>

# 效果
![](images\image.png)

# 使用

## 引入组件
```json
  "usingComponents": {
    "image-cropper":"/image-cropper/image-cropper"
  },
  "allowsBounceVertical":"NO" //记得将页面拖动设置为NO
```
## page.axml

``` html
<image-cropper a:if="{{true}}}" imgSrc="{{src}}" ref="imagecropper" id="image-cropper" limit_move="{{true}}" disable_rotate="{{true}}" width="{{width}}" height="{{height}}" onLoadimage="loadimage" onConfirm="handleCut" onCancle="handleCancle"></image-cropper>
```

## page.js
```js
data{
    src: "" ,
    width: 250, //宽度
    height: 250, //高度
},
imagecropper(ref) {
    this.cropper = ref;
},
//加载图片
loadimage(e) {
    console.log('图片加载完成', e);
    my.hideLoading();
    //重置图片角度、缩放、位置
    this.cropper.imgReset();
  },
//裁剪
handleCut(e){
    console.log("裁剪/确认",e)
},
//取消
handleCancle(){
    console.log("取消")
}
```

### handleCut(e)
返回值e:
```
{
    url: ,//临时文件地址
    width:,//宽度
    height:,//高度
}
```
url的使用参考[文件系统](https://opendocs.alipay.com/mini/03dof7?pathHash=0bf754be)


# 图片裁剪组件配置说明

| 配置项名称       | 类型       | 默认值       | 描述                                                                 |
|------------------|------------|--------------|----------------------------------------------------------------------|
| `onCropperload`  | Function   | null         | 组件加载完成时触发的回调函数。                                      |
| `onLoadimage`    | Function   | null         | 图片加载完成时触发的回调函数。                                      |
| `onConfirm`      | Function   | null         | 用户确认裁剪操作时触发的回调函数。                                  |
| `onCancle`       | Function   | null         | 用户取消裁剪操作时触发的回调函数。                                  |
| `imgSrc`         | String     | ""           | 要裁剪的图片路径。                                                  |
| `height`         | Number     | 200          | 裁剪框的高度。                                                      |
| `width`          | Number     | 200          | 裁剪框的宽度。                                                      |
| `min_width`      | Number     | 64           | 裁剪框的最小宽度。                                                  |
| `min_height`     | Number     | 64           | 裁剪框的最小高度。                                                  |
| `max_width`      | Number     | 300          | 裁剪框的最大宽度。                                                  |
| `max_height`     | Number     | 300          | 裁剪框的最大高度。                                                  |
| `disable_width`  | Boolean    | false        | 是否禁止调整裁剪框的宽度。                                          |
| `disable_height` | Boolean    | false        | 是否禁止调整裁剪框的高度。                                          |
| `disable_ratio`  | Boolean    | false        | 是否锁定裁剪框的比例（宽高比）。                                    |
| `export_scale`   | Number     | 3            | 生成的图片尺寸相对于裁剪框的比例。                                  |
| `quality`        | Number     | 1            | 生成的图片质量（范围为0到1）。                                      |
| `scale`          | Number     | 1            | 图片的缩放比例。                                                    |
| `angle`          | Number     | 0            | 图片的旋转角度。                                                    |
| `min_scale`      | Number     | 0.5          | 图片的最小缩放比例。                                               |
| `max_scale`      | Number     | 2            | 图片的最大缩放比例。                                               |
| `disable_rotate` | Boolean    | false        | 是否禁用图片旋转功能。                                              |
| `limit_move`     | Boolean    | false        | 是否限制裁剪框的移动范围（裁剪框只能在图片内）。                    |

---

## 说明
以上配置项用于自定义图片裁剪组件的行为和外观。开发者可以根据需求调整这些选项以实现特定的功能。

本项目来修改自![alipaycrop]https://github.com/YYBT/alipaycrop 由于原组件在使用过程中存在一些问题，所以进行部分修改，支付宝端运行良好，事件原因，微信尚未测试（大概率运行不了，有些函数支付宝和微信不一样）。



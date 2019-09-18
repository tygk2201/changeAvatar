用法：

```javascript
//template部分
<cropper selWidth="660rpx" selHeight="660rpx" @upload="myUpload" :avatarSrc="imgurl" avatarStyle="width:100vw;height:100vw;"> 
</cropper>


//script部分
	import cropper from "../../components/cropper.vue";
	export default {
		components: {
		  cropper
		},
		data() {
			return {
				 imgurl:"/static/logo.png"
			}
		},
		methods: {
			//上传返回图片
			myUpload(rsp) {
			  const self = this;
			  self.imgurl = rsp.path; //更新头像方式一
			  // rsp.avatar.imgSrc = rsp.path; //更新头像方式二
			},

		}
	}
```

| 属性        | 必须 | 说明                                                         |
| :---------- | ---- | ------------------------------------------------------------ |
| selWidth    | 是   | 裁剪区域的宽                                                 |
| selHeight   | 是   | 裁剪区域的高                                                 |
| avatarSrc   | 否   | 头像地址                                                     |
| avatarStyle | 否   | 头像样式，默认{width:100vw;height:100vw;}                    |
| expWidth    | 否   | 设置导出的图片宽度                                           |
| expHeight   | 否   | 设置导出的图片高度                                           |
| quality     | 否   | 生成图片质量，取值范围0~1，默认0.9                           |
| minScale    | 否   | 缩放允许的最小比例，默认0.3                                  |
| maxScale    | 否   | 缩放允许的最大比例，默认4                                    |
| canScale    | 否   | 是否允许缩放，默认true                                       |
| noTab       | 否   | 是否存在tabBar，默认false，主要为了去除报错存信息，不设置也不影响使用 |
| index       | 否   | 索引，回调upload方法，返回该index值，默认undefined           |

| 事件    | 必须 | 说明                                                         |
| ------- | ---- | ------------------------------------------------------------ |
| upload  |      | 在点击上传后调用<br>返回格式 {avatar: xx, path: xx, index: xx, data: xx}
avatar: 对象类型，可以通过更新imgSrc值，更新头像
path: 临时头像地址
index: 索引 |
| avtinit |      | 在图片选择后调用，可用于自定义操作，例如禁用下拉刷新，点击上传后再启用 |


# 示例

```javascript
	uniapp 引用 import CTabbar from "../../components/Chad-CTabbar/Chad-CTabbar.vue"

	vue npm安装引用 import CTabbar from 'chad-tabbar'
	components: {
			CTabbar
	}
	<CTabbar 
		:tabbarList="tabbarList" 
		:MainColor="'#d4237a'"
		:ViceColor="'#7f8c8d'"
		@currentClick="currentClick" />
```
	-  tabbarList: [{
						ImgUrl: '/static/c-tabbar/img/home.png',
						AcImgUrl:"/static/c-tabbar/img/home-c.png",
						text: '首页',
						router: '/agency',
					},
					{
						ImgUrl: '/static/c-tabbar/img/cart.png',
						AcImgUrl:"/static/c-tabbar/img/cart-c.png",
						text: '购物车',
						router: '/census',
					},
					{
						ImgUrl: '/static/c-tabbar/img/hot.png',
						AcImgUrl:"/static/c-tabbar/img/hot-c.png",
						text: '热门',
						router: '/workbench',
					},
					{
						ImgUrl: '/static/c-tabbar/img/file.png',
						AcImgUrl:"/static/c-tabbar/img/file-c.png",
						text: '文件',
						router: '/addressbook',
					},
					{
						ImgUrl: '/static/c-tabbar/img/my.png',
						AcImgUrl:"/static/c-tabbar/img/my-c.png",
						text: '我的',
						router: '/my',
					},
				]
			
# tip
 vue  引用 需要 安装 node-sass 和 sass-loader
 ```
  npm i -D node-sass sass-loader
 ```

# todo
 此版本仅支持5项tabbar
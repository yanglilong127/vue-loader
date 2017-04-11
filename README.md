# vue-loader [![Build Status](https://circleci.com/gh/vuejs/vue-loader/tree/master.svg?style=shield)](https://circleci.com/gh/vuejs/vue-loader/tree/master) [![Windows Build status](https://ci.appveyor.com/api/projects/status/8cdonrkbg6m4k1tm/branch/master?svg=true)](https://ci.appveyor.com/project/yyx990803/vue-loader/branch/master) [![npm package](https://img.shields.io/npm/v/vue-loader.svg?maxAge=2592000)](https://www.npmjs.com/package/vue-loader)

> Vue.js component loader for [Webpack](http://webpack.github.io).

**NOTE: the master branch (9.0+) only works with Vue 2.x. For usage with Vue 1.x, see the [8.x branch](https://github.com/vuejs/vue-loader/tree/8.x).**

It allows you to write your components in this format:

![screenshot](http://blog.evanyou.me/images/vue-component.png)

The best way to get started is with [vue-cli](https://github.com/vuejs/vue-cli):

``` js
npm install -g vue-cli
vue init webpack-simple hello
cd hello
npm install
npm run dev
```

This will setup a basic Webpack + `vue-loader` project for you, with `*.vue` files and hot-reloading working out of the box!

For advanced `vue-loader` configuration, checkout the [documentation](http://vuejs.github.io/vue-loader/index.html).

#MVVM:  view  viewmodel model
	1.是一个轻量级MVVM框架
	2.数据驱动+组件化的前端开发
	3.Github超过25K+的star数，社区完善
	优点：Vue.js更轻量   更易上手   吸取了两家之长

	数据驱动  DOM是数据的一种自然映射
	npm install --g vue-cli安装包后使用vue命令可能出现：vue不是内部或外部命令；
	解决办法：搜索vue.cmd的位置，搜索到这个批处理文件后把这个文件的路径加入Path中就行了
#Vue-cli是Vue的脚手架工具    帮助我们写好Vue.js基础代码的工具
	作用：目录结构、本地调试、代码部署、热加载、单元测试
	使用方法：
		1.vue init webpack webapp (初始化使用webpack模版，项目名称为webapp)
		2.  （1）项目名 webapp
			（2）增加一个描述：my webapp
			（3）作者：
			（4）ES6代码风格检查器：Y
			（5）标准：Standrad
			（6）前端界面测试库：no
			（7）no
		3.cd webapp
		4.npm install
		5.npm run dev


		#项目搭建：
		1.写css文件直接用stylus语法，将css后缀名改为styl
		语法规则是将css文件里的所有'{}'大括弧和';'号删掉
		2.在build下的dev-server.js文件里面增加路由信息
			在var app = express()语句后面增加以下语句
			var appData=require('../data.json');
			var seller=appData.seller;
			var goods=appData.goods;
			var ratings=appData.ratings;

			var apiRouters=express.Router();

			apiRouters.get('/seller',function(req,res){
			  res.json({
			    errno:0,
			    data:seller
			  });
			});

			apiRouters.get('/goods',function(req,res){
			  res.json({
			    errno:0,
			    data:goods
			  });
			});

			apiRouters.get('/ratings',function(req,res){
			  res.json({
			    errno:0,
			    data:ratings
			  });
			});

			app.use('/api',apiRouters);
		启动服务后在浏览器地址栏输入localhost:8080/api/seller查看是否有返回数据
		3.在static目录下新建一个css文件夹，文件夹下放reset.css文件
			在index.html文件里面引用reset.css样式文件
			##css reset的作用和用途："覆盖"浏览器的CSS默认属性。最最简单的说法就是把浏览器提供的默认样式覆盖掉!这就是CSS reset。
		4.在.eslintrc.js文件里面添加语句：
			'semi':['error','always'],    //配置入口文件main.js中可以使用分号
			'indent':0      //缩进空格取消


	#vue-loader:
		broserrify  模块加载，只能加载js
		webpack  模块加载器，一切东西都是模块，最后打包到一块

		require('style.css');    ->  css.loader、style.loader

		##vue-loader基于wepack
			.vue文件
				放置的是vue组件代码
				<template>
					html
				</template>

				<style>
					css
				</style>

				<script>
					js  (平时代码  ES6)  babel-loader转换为ES5
				</script>
		##简单的目录结构
			|-index.html
			|-main.js    入口文件
			|-App.vue    vue文件
			|-package.json   工程文件（项目依赖、名称、配置）
			|-webpack.config.js   wenpack配置文件

		webpack准备工作：
			npm install webpack --save-dev
			npm install webpack-dev-server --save-dev
			下载完后将package.json文件里面更改内容
				"scripts": {
					    "dev": "webpack-dev-server --inline --hot --port 8082",
					    "build":"webpack -p"    //打包并编译
					  }
			App.vue   ->代码正常化   vue-loader  
						npm install vue-loader --save-dev
			vue-html-loader、css-loader、vue-style-loader、vue-hot-reload-api

			babel-loader
			babel-core
			babel-plugin-transform-runtime
			babel-preset-es2015
			babel-runtime

			最核心：npm install vue --save-dev



		#ES6模块化开发
			导出文件：export default{}
			引入文件：import name from './address'


		#//专门配置路由规则

		//引入模块    
		import Home from './components/home.vue'
		import News from './components/news.vue'

		export default{
			'/home':{
				component:Home
			},
			'/news':{
				component:News
			} 
		}

		然或在main.js中引入路由配置
		import routerConfig from './router.config.js'
		//配置路由
		const router=new VueRouter();
		router.map(routerConfig);

		上线：执行此命令npm run build   本质就是执行  -> webpack -p 

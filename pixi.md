###别名###
	var Container = PIXI.Container,
		Sprite = PIXI.Sprite,
		Rectangle = PIXI.Rectangle,
		TextureCache = PIXI.utils.TextureCache,
		autoDetectRenderer = PIXI.autoDetectRenderer,
		loader = PIXI.loader,
		Resources = PIXI.loader.resources;		
===
###固定模式###

####1.创建渲染器####
	var renderer = PIXI.autoDetectRenderer(256,256);
	
####2.添加canvas到html文档####
	document.body.appendChild(renderer.view)
	
####3.创建stage容器####
	var stage = new PIXI.Container();

####4.渲染节点####
	renderer.render(stage);
===
###一些名词###
	渲染器:  renderer
	根容器:  stage
	精灵:    sprite
	纹理缓存: TextureCache===###一些关系###
####PIXI -> Container -> stage####
	var stage = new PIXI.Containter();
####PIXI -> utils -> TextureCache####
	//从纹理中创建精灵：
	var texture = PIXI.utils.TextureCache["images/cat.png"];
	var sprite = new PIXI.Sprite(texture);####PIXI -> Sprite####
####PIXI -> loader -> resources -> texture####	PIXI.loader.add("images/01.png").add("images/02.png").load(setup);	//或者	var sprite = new PIXI.Sprite(PIXI.loader.resources["images/cat.png"].texture);	####PIXI -> Texture########PIXI -> BaseTexture -> formCanvas####
	var base = new PIXI.BaseTexture(anyImageObject),
		texture = new PIXI.Texture(base),
		sprite = new PIXI.Sprite(texture);
	//或者
	var base = new PIXI.BaseTexture.fromCanvas(anyCanvasElement);
===
###操作精灵cat###
	stage.addChild(cat); // 添加精灵到场景
	stage.removeChild(cat); //移除精灵
	cat.visible = false;  //隐藏精灵
	cat.x = 96; //设置精灵的x坐标
	cat.y = 96; //设置精灵的y坐标
	cat.position.set(96, 96); //设置精灵的坐标
	cat.width = 80; //设置精灵的宽
	cat.height = 120; //设置精灵的高
	cat.scale.x = 0.5; // 把精灵x缩小一半
	cat.scale.y = 0.5; // 把精灵y缩小一半
	cat.scale.set(0.5, 0.5); //把精灵缩小一半
	cat.scale.x = 2; // 把精灵x放大一倍
	cat.scale.y = 2; // 把精灵y放大一倍
	cat.scale.set(2, 2); //把精灵放大一倍
	cat.rotation = 0.5; //精灵旋转弧度，默认锚点为左上角	cat.anchor.x = 0.5; //精灵围绕中心旋转
	cat.anchor.y = 0.5; //精灵围绕中心旋转
	cat.anchor.set(0.5,0.5); //精灵围绕中心旋转
	cat.pivot.set(cat.width * 0.5, cat.height * 0.5); //支点(pivot)是锚点的像素单位
	cat.pivot.anchor.set(0.5, 0.5); //支点(pivot)可以认为是锚点的像素单位
	cat.vx = 2 // 精灵在x上的速度是2
	cat.vy = 2 // 精灵在y上的速度是2
	cat.director = 1 //精灵的方向1或者－1
===
###抠图###
	//加载图片完成的回调,方法均使用别名
	var texture = TextureCache['images/tileset.png']
	var rectangle = new Rectangle(192,168,64,64);
	texture.frame = rectangle
	var rocker = new Sprite(texture)
===
###加载精灵表单###
	loader.add("images/trasureHunter.json").load(setup);
===
###碰撞检测###
	hitTestRectangle(cat1, cat2)
===
###更多辅助工具###
- [Bump](https://github.com/kittykatattack/bump): 2D 碰撞组件
- [Tink](https://github.com/kittykatattack/tink): 拖拽以及交互相关组件
- [Charm](https://github.com/kittykatattack/charm): 移动组件
- [Dust](https://github.com/kittykatattack/dust): 粒子效果组件
- [Sprite Utilities](https://github.com/kittykatattack/spriteUtilities): 更简单创建以及使用精灵，附加一个状态机和动画
- [Sound.js](https://github.com/kittykatattack/sound.js): 声音特效组件
- [Smoothie](https://github.com/kittykatattack/smoothie): 超顺滑精灵动画工具，使用时间插值方法。指定游戏的fps，完全独立于精灵渲染和游戏逻辑。

你可以在 《[Learn PixiJS](http://www.springer.com/us/book/9781484210956)》 这本书中找到以上组件的使用方法。	
          ￼                                                          
                                                                                                      
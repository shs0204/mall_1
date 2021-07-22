# mall


### 五. 对滚动进行重构: Better-Scroll

#### 5.1. 在index.html中使用Better-Scroll

* const bscroll = new BScroll(el, {   })
* 注意: wrapper -> content -> 很多内容
* 1.监听滚动
  * probeType: 0/1/2(手指滚动)/3(只要是滚动)
  * bscroll .on('scroll', (position) => {})
* 2.上拉加载
  * pullUpLoad: true
  * bscroll .on('pullingUp', () => {})
* 3.click: false
  * button可以监听点击
  * div不可以

#### 5.2. 在Vue项目中使用Better-Scroll

* 在Profile.vue中简单的演示
* 对Better-Scroll进行封装: Scroll.vue
* Home.vue和Scroll.vue之间进行通信
  * Home.vue将probeType设置为3
  * Scroll.vue需要通过$emit, 实时将事件发送到Home.vue

### 六. 回到顶部BackTop

#### 6.1. 对BackTop.vue组件的封装



#### 6.2. 如何监听组件的点击

* 直接监听back-top的点击, 但是可以直接监听?
  * 不可以, 必须添加修饰.native
* 回到顶部
  * scroll对象, scroll.scrollTo(x, y, time)
  * this.$refs.scroll.scrollTo(0, 0, 500)



#### 6.3. BackTop组件的显示和隐藏 

* isShowBackTop: false
* 监听滚动, 拿到滚动的位置:
  * -position.y > 1000  -> isShowBackTop: true
  * isShowBackTop = -position.y > 1000
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

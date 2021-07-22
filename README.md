Coderwhy老师的移动端购物商城项目

### 一. 首页商品数据的请求

#### 1.1. 设计数据结构, 用于保存数据

goods: {

pop: page/list

new: page/list

sell: page/list

}



#### 1.2. 发送数据请求

* 在home.js中封装getHomeGoods(type, page)
* 在Home.vue中, 又在methods中getHomeGoods(type)
* 调用getHomeGoods('pop')/getHomeGoods('new')/getHomeGoods('sell')
  * page: 动态的获取对应的page
* 获取到数据: res
  * this.goods[type].list.push(...res.data.list)
  * this.goods[type].page += 1

goods: {

pop: page1:/list[30]

new: page1/list[30]

sell: page1/list[30]

}

### 二. 对商品数据进行展示

#### 2.1. 封装GoodsList.vue组件

* props: goods -> list[30]
* v-for goods -> GoodsListItem[30]
* GoodListItem(组件) -> GoodsItem(数据)



#### 2.2. 封装GoodsListItem.vue组件

* props: goodsItem 
* goodsItem 取出数据, 并且使用正确的div/span/img基本标签进行展示



### 三. 对滚动进行重构: Better-Scroll

#### 3.1. 在index.html中使用Better-Scroll

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

#### 3.2. 在Vue项目中使用Better-Scroll

* 在Profile.vue中简单的演示
* 对Better-Scroll进行封装: Scroll.vue
* Home.vue和Scroll.vue之间进行通信
  * Home.vue将probeType设置为3
  * Scroll.vue需要通过$emit, 实时将事件发送到Home.vue

### 四. 回到顶部BackTop

#### 4.1. 对BackTop.vue组件的封装



#### 4.2. 如何监听组件的点击

* 直接监听back-top的点击, 但是可以直接监听?
  * 不可以, 必须添加修饰.native
* 回到顶部
  * scroll对象, scroll.scrollTo(x, y, time)
  * this.$refs.scroll.scrollTo(0, 0, 500)



#### 4.3. BackTop组件的显示和隐藏 

* isShowBackTop: false
* 监听滚动, 拿到滚动的位置:
  * -position.y > 1000  -> isShowBackTop: true
  * isShowBackTop = -position.y > 1000

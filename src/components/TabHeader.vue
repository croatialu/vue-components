<template>
  <div>
    <!-- container -->
    <div class="container">
      <div class="listWrap">
        <div class="listItem" v-for=" ( item, index ) in titleList" :key="index" @click="onItemClick">{{item}}</div>
        <div class="scrollBar" :style="{ left: scrollBarLeft, width: scrollBarWidth }"></div>
      </div>
    </div>


  </div>
</template>


<script>
export default {
  data(){
    return {
      titleList: [ '推荐分类', '京东超市', '国际名牌', '奢侈品', '海屯全球', '唯品会', '男装', '女装', '男鞋','女鞋', '内衣配饰', '箱包手袋', '美妆护肤', '个护清洁', '钟表珠宝', '手机数码', ],
      scrollBarWidth: 0,
      scrollBarLeft: 0,
    }
  },
  created(){

  },
  mounted(){

  },
  methods: {
    onItemClick( e ){
      // console.log( e )
      const {  } = e.target
    }
  }
}
</script>


<style>

.listWrap {
  display: flex;
  overflow-x: auto;
  position: relative;
}

.listWrap::-webkit-scrollbar{
  display: none;
}

.listItem{
  word-break: keep-all;
  padding: .1rem;
}

.scrollBar{
  position: absolute;
  left: 0;
  bottom: 0;
  width: 1rem;
  height: .02rem;
  background-color: skyblue;
}

</style>

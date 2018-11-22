<template>
  <div>
    <div class="container" ref="container">
      <div class="listWrap" ref="listWrap" :style="{ transform: `translateX(${listWrapTranslateX})` }">
        <div class="listItem" v-for=" ( item, index ) in titleList" :key="index" @click="onItemClick">
          {{ item }}
        </div>
        <div class="scrollBar" :style="{ left: scrollBarLeft, width: scrollBarWidth,  transition: '.3s all' }" ></div>
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
      listWrapTranslateX: 0
    }
  },
  created(){

  },
  mounted(){

  },
  methods: {
    onItemClick( e ){
      console.log(e)
      const { offsetWidth, offsetLeft, clientWidth, clientLeft } = e.target;
      this.scrollBarWidth = `${offsetWidth}px`;
      this.scrollBarLeft = `${offsetLeft}px`;


      this.startMove(offsetLeft - window.innerWidth / 2 + clientWidth / 2)
    },

    startMove(distance){
      // this.$refs.listWrap.scrollLeft = `${distance}px`
      let _distance = this.$refs.container.scrollLeft;
      let count = 0;
      if( _distance > distance ){
        // 往左
        count = -10;
      }else {
        // 往右
        count = 10;
      }
      clearInterval( this.timer )
      this.timer = setInterval(() => {
        this.$refs.container.scrollTo( _distance, 0 )
        _distance = _distance + count;


        if( (_distance >= distance && count > 0) || (_distance <= distance && count < 0) ){
          clearInterval( this.timer )
        }
      }, 20);

    }
  }
}
</script>


<style>
  .container {
    overflow-x: scroll;
  }
  .listWrap {
    position: relative;
    display: inline-block;
    white-space: nowrap;
    transition: .3s all;
  }

  .container::-webkit-scrollbar {
      display: none;
  }
  .listItem {
    display: inline-block;
    padding: .1rem;
    word-break: keep-all;
  }


  .scrollBar {
    width: 1rem;
    position: absolute;
    bottom: 0;
    height: .02rem;
    background-color: skyblue;
  }
</style>


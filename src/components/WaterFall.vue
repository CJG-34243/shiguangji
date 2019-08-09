<template>
  <div class="container-water-fall">
    <waterfall
      :col="col"
      :width="itemWidth"
      :gutterWidth="gutterWidth"
      :data="imageData"
      @loadmore="loadmore"
      @scroll="scroll"
    >
      <template>
        <div class="cell-item" v-for="(item,index) in imageData" :key="index">
          <img
            v-if="item.photo"
            :src="item.photo"
            alt="加载错误"
            @click="dscr(item.photo,item.babyName,item.story)"
          />
          <!--<img v-if="item.img" :lazy-src="item.img" alt="加载错误"  />   //lazy-src 懒加载 -->
          <div class="item-body">
            <div class="item-desc">{{item.babyName}}</div>
            <div class="item-footer">
              <!-- <div class="avatar" :style="{backgroundImage : `url(${item.avatar})` }"></div> -->
              <!-- <div class="name">{{item.user}}</div> -->
              <div class="like" :class="item.liked?'active':''">
                <div class="like-total">{{item.liked}}</div>
              </div>
            </div>
          </div>
        </div>
      </template>
    </waterfall>

    <van-dialog v-model="show" :title="bname">
      <img :src="imgurl" style="width:100%;height:100%" />
      <p>{{bstory}}</p>
    </van-dialog>
    <!-- <van-popup v-model="show">
      <div style="width:8rem;height:15rem">
        
      </div>
    </van-popup>-->
  </div>
</template>


<script>
import axios from "axios";
export default {
  data() {
    return {
      imageData: [],
      col: 2,
      itemWidth: 0,
      gutterWidth: 0,
      show: false,
      imgurl: "",
      bname: "",
      bstory: ""
    };
  },

  methods: {
    scroll(scrollData) {
      // console.log(scrollData);
    },
    loadmore(index) {
      // this.data = this.data.concat(this.data);
    },
    dscr(a, b, c) {
      this.show = true;
      console.log(a);
      this.imgurl = a;
      this.bname = b;
      this.bstory = c;
      console.log(this.imageData);
    }
  },
  mounted() {
    // console.log(456);
    axios
      .get("http://106.12.11.4:8888/ShiGuangJi/shiguangji/yunphoto.do")
      .then(res => {
        this.imgurl = res.data.data.photo;
        this.imageData = res.data.data;
      })
      .catch(function(error) {
        console.log(error);
      });
  }
};
</script>


<style scoped>
.cell-item {
  padding: 0.2rem;
  overflow: hidden;
}
.cell-item img {
  width: 100%;
  height: 100%;
  border-radius: 1rem;
}
.van-dialog__header {
  padding: 0rem;
}
</style>





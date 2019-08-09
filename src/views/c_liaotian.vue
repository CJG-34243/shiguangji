<template>
  <div>
    <div style=" display: flex;flex-direction: column;overflow:auto;">
      <!-- 头部导航 -->
      <van-nav-bar
       fixed
        :title="title"
        left-arrow
        @click-left="onClickLeft"
        class="wd-nav"
        style="height:55px;line-height:55px"
      />
    </div>
    <div style="margin:55px 10px 59px;overflow:auto;" id="ltk">

      <ul style="width:100%-20px;flex:1;" ref="hello">
      <!-- 1 -->
      <li style="width:100%;padding-bottom:10px;" v-for="(item,index) in message_array" v-bind:key="index">
        <div v-if="index%2 == 0" style="min-height:110px;">
          <div style="height:55px">
          <van-image
            width="50"
            height="50"
            src="http://b-ssl.duitang.com/uploads/item/201703/12/20170312000617_hGkP8.thumb.700_0.jpeg"
            style="border-radius:50%;overflow: hidden;float:right;margin-left:10px;"
          />
          <span style="float:right;">{{item.sj}}</span>
        </div>
        <p style="min-height:30px;border:1px solid #cecece;border-radius:4px;line-height:30px;font-size:14px;margin-top:10px;float:right;padding:0 5px;">{{item.par}}</p>
        </div>
        <div v-if="index%2 != 0" style="min-height:110px;">
          <div style="height:55px">
          <van-image
            width="50"
            height="50"
            src="http://b-ssl.duitang.com/uploads/item/201504/21/20150421H4553_BTtkK.jpeg"
            style="border-radius:50%;overflow: hidden;float:left;margin-right:10px;"
          />
          <span style="float:left;margin:5px 10px 0 0;">{{item.sg}}</span>
        </div>
        <p style="min-height:30px;border:1px solid #cecece;border-radius:4px;line-height:30px;font-size:14px;margin-top:10px;float:left;padding:0 5px;">{{item.prr}}</p>
        </div>
        
      </li>
    </ul>

    </div>
    
    <div>
      <van-goods-action style="height:38px;padding:10px 0;border-top:1px solid #cecece;">
        <van-goods-action-icon icon="chat-o" @click="onClickIcon" />
        <!-- 228 -->
        <input
          type="text"
          style="width:242px;height:35px;border:1px solid #cecece;border-radius:10px;"
          v-model="message"
          id="btn"
        />
        
        <van-button  round type="primary" @click="dealMessage" style="height:37px;line-height:37px;margin:0 10px;">发送</van-button>
        
      </van-goods-action>
    </div>
  </div>
</template>

<script>
import { Toast } from "vant";
import axios from "axios";
export default {
  name: "c_liaotian",
  data() {
    return {
      title: this.$route.params.id,
      message: "",
      message_array: [],
      //time:"11:11",
    };
  },
  mounted() {
   
  },
  updated() {
    
  },
  methods: {
    onClickLeft() {
      this.$router.go(-1);
    },
    onClickButton() {
      Toast("点击购物");
    },
    onClickIcon() {
      Toast("点击按钮");
    },
    dealMessage: function() {
      var obtn=document.getElementById("btn");
      let oDate = new Date();
      let xs=oDate.getHours();
      let fz=oDate.getMinutes();
      let hm=oDate.getSeconds();
      if(xs<10&&xs>=0){
      xs="0"+xs;
      }else{
      xs=xs
      }
      if(fz<10&&fz>=0){
      fz="0"+fz;
      }else{
      fz=fz
      }
      if(hm<10&&hm>=0){
      hm="0"+hm;
      }else{
      hm=hm
      } 
      let time=xs+":"+fz+":"+hm;
      if(obtn.value==""){
         Toast('内容不能为空');
      }else{
        this.message_array.push({par:this.message,sj:time});
        var tag = this.message;
        this.message = "";
        this.$nextTick(() => {
        var ltk = document.getElementById("ltk"); //获取dom
        ltk.scrollTop = ltk.offsetHeight;
        });
      }
        axios //请求人工智障接口
        .get("http://i.itpk.cn/api.php", {
        params: {
        question: tag,
        api_key: "6d6f6e2ba4d88377b54107e29047994b",
        api_secret: "6w3h17ufope0"
        }
        })
        .then(ret => {
        let oDate = new Date();
        let xs=oDate.getHours();
        let fz=oDate.getMinutes();
        let hm=oDate.getSeconds();
        if(xs<10&&xs>=0){
        xs="0"+xs;
        }else{
        xs=xs
        }
        if(fz<10&&fz>=0){
        fz="0"+fz;
        }else{
        fz=fz
        }
        if(hm<10&&hm>=0){
        hm="0"+hm;
        }else{
        hm=hm
        } 
        let time=xs+":"+fz+":"+hm;
        this.message_array.push({prr:ret.data,sg:time});
        })
        .then(() => {
        ltk.scrollTop = ltk.scrollHeight;
        });
     
    }
  }
};
</script>
<style scoped>
#ltk{
  height:550px;
}
</style>
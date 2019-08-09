<template>
  <div>
    <van-nav-bar
      left-text="返回"
      right-text="完成"
      left-arrow
      @click-left="onClickLeft"
      @click-right="onClickRight"
    />
    <van-uploader v-model="fileList" :after-read="afterRead" multiple="ture" :max-count="5"></van-uploader>
  </div>
</template>

<script>
export default {
  name: "topicture",
  data() {
    return {
      fileList: [{ url: "https://img.yzcdn.cn/vant/cat.jpeg" }]
    };
  },
  components: {},
  methods: {
    beforeRead(file) {
      if (file.type !== "image/jpg/png/jpeg") {
        alert("请上传 jpg 格式图片");
        return false;
      }
      return true;
    },
    afterRead(file) {
      console.log(this.fileList);
    },
    onClickLeft() {
      this.$router.push({ name: "dcim" });
    },
    onClickRight() {
      alert("完成");
    }
  }
};
</script>
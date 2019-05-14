<template>
  <div class="app">
    <!--<mce-editor 
    :config           = "Config"
     v-model          = "Value"
    :url              = "Url" //图片上传地址
    :max-size         = "MaxSize"//文件上传最大值
    :accept           = "Accept"//接收什么格式的图片
    :with-credentials = false
    @on-ready         = "onEditorReady"//后面什么的没研究了
    @on-destroy       = "onEditorDestroy"
    @on-upload-success= "onEditorUploadComplete"
    @on-upload-fail   = "onEditorUploadFail"
    ></mce-editor>-->

    <mceeditor v-model="Value"></mceeditor>
		 <div class="home-phone-copy">
        <button type="button" class="home-phone-butt" @click="copyText">复制</button>
    </div>
		Value:
    <span class="btn-copy">{{Value}}</span>
   
  </div>
</template>

<script>
import mceeditor from "@/components/mceeditor";
window.tinymce.baseURL = "/static/tinymce";
window.tinymce.suffix = ".min";
export default {
  components: {
    mceeditor
  },
  data() {
    return {
      Value: "",
      alertText: false
    };
  },
  methods: {
    copyText() {
      //this.clidata是要复制的动态数据
      this.$copyText(this.Value).then(
        () => {
          console.log("复制成功" + this.clidata);
        },
        () => {
          console.log("复制失败了");
        }
      );
    }
  }
};
</script>

<style>
.app {
  width: 1204px;
  margin: 0 auto;
}
.btn-copy {
  padding: 2px 4px;
  font-size: 12px;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 4px;
}
.btn-copy-success {
  padding: 2px 4px;
  font-size: 12px;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 4px;
}
</style>
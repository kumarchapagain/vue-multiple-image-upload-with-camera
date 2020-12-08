<template>
  <div id="app">
    <div style="display: flex; justify-content: center;">
      <v-camera
          @upload-success="uploadImageSuccess"
          @edit-image="editImage"
          @mark-is-primary="markIsPrimary"
          @limit-exceeded="limitExceeded"
          @before-remove="beforeRemove"
          id-upload="myIdUpload"
          edit-upload="myIdEdit"
          :max-image=3
          :video-height=200
          :video-width= 190
          :canvas-height= 337.5
          :canvas-width= 450
          :camera=true
          primary-text=""
          browse-text="Browse picture(s)"
          drag-text="Drag pictures"
          drop-text="Drop your file here ..."
          mark-is-primary-text="Set as default"
          popup-text=""
          :multiple=true
          :show-edit=true
          :show-delete=true
          :show-add=true
      ></v-camera>
    </div>
  </div>
</template>

<script>
import MultipleImageUpload from './components/MultipleImageUpload.vue'

export default {
  name: 'App',
  components: {
    VCamera: MultipleImageUpload
  },
  methods: {
    uploadImageSuccess(formData, index, fileList) {
      console.log('data', formData, index, fileList)
      // Upload image api
      // axios.post('http://your-url-upload', formData).then(response => {
      //   console.log(response)
      // })
    },
    beforeRemove(index, removeCallBack) {
      console.log('index', index)
      var r = confirm("remove image")
      if (r == true) {
        removeCallBack()
      } else {
      }
    },
    editImage(formData, index, fileList) {
      console.log('edit data', formData, index, fileList)
    },
    markIsPrimary(index, fileList){
      console.log('markIsPrimary data', index, fileList)
    },
    limitExceeded(amount){
      console.log('limitExceeded data', amount)
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

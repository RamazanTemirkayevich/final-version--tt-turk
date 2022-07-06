<script>
export default {
  name: "VueUploadImages", // vue component name
  data() {
    return {
      error: "",
      files: [],
      dropped: 0,
      Imgs: [],
    };
  },
  props: {
    max: Number,
    uploadMsg: String,
    maxError: String,
    fileError: String,
    clearAll: String,
  },
  methods: {
    dragOver() {
      this.dropped = 2;
    },
    dragLeave() {},
    drop(e) {
      let status = true;
      let files = Array.from(e.dataTransfer.files)
      if (e && files) {
        files.forEach((file) => {
          if (file.type.startsWith("image") === false) status = false;
        });
        if (status == true) {
          if (
            this.$props.max &&
            files.length + this.files.length > this.$props.max
          ) {
            this.error = this.$props.maxError
              ? this.$props.maxError
              : `Maximum files is` + this.$props.max;
          } else {
            this.files.push(...files);
            this.previewImgs();
          }
        } else {
          this.error = this.$props.fileError
            ? this.$props.fileError
            : `Unsupported file type`;
        }
      }
      this.dropped = 0;
    },
    append() {
      this.$refs.uploadInput.click();
    },
    readAsDataURL(file) {
      return new Promise(function (resolve, reject) {
        let fr = new FileReader();
        fr.onload = function () {
          resolve(fr.result);
        };
        fr.onerror = function () {
          reject(fr);
        };
        fr.readAsDataURL(file);
      });
    },
    deleteImg(index) {
      this.Imgs.splice(index, 1);
      this.files.splice(index, 1);
      this.$emit("changed", this.files);
      this.$refs.uploadInput.value = null;
    },
    previewImgs(event) {
      if (
        this.$props.max &&
        event &&
        event.currentTarget.files.length + this.files.length > this.$props.max
      ) {
        this.error = this.$props.maxError
          ? this.$props.maxError
          : `Maximum files is` + this.$props.max;
        return;
      }
      if (this.dropped == 0) this.files.push(...event.currentTarget.files);
      this.error = "";
      this.$emit("changed", this.files);
      let readers = [];
      if (!this.files.length) return;
      for (let i = 0; i < this.files.length; i++) {
        readers.push(this.readAsDataURL(this.files[i]));
      }
      Promise.all(readers).then((values) => {
        this.Imgs = values;
      });
    },
    reset() {
      this.$refs.uploadInput.value = null;
      this.Imgs = [];
      this.files = [];
      this.$emit("changed", this.files);
    },
  },
};
</script>

<template>
  <div
    class="container"
    @dragover.prevent="dragOver"
    @dragleave.prevent="dragLeave"
    @drop.prevent="drop($event)"
  >
    <div class="drop" v-show="dropped == 2"></div>
    <!-- Error Message -->
    <div v-show="error" class="error">
      {{ error }}
    </div>

    <!-- To inform user how to upload image -->
    <div  class="beforeUpload">
      <input
        type="file"
        style="z-index: 1"
        accept="image/*"
        ref="uploadInput"
        @change="previewImgs"
        multiple
      />
      <svg width="23" height="23" viewBox="0 0 23 23" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M20.875 9.15625H13.8438V2.125C13.8438 1.26221 13.144 0.5625 12.2812 0.5625H10.7188C9.85596 0.5625 9.15625 1.26221 9.15625 2.125V9.15625H2.125C1.26221 9.15625 0.5625 9.85596 0.5625 10.7188V12.2812C0.5625 13.144 1.26221 13.8438 2.125 13.8438H9.15625V20.875C9.15625 21.7378 9.85596 22.4375 10.7188 22.4375H12.2812C13.144 22.4375 13.8438 21.7378 13.8438 20.875V13.8438H20.875C21.7378 13.8438 22.4375 13.144 22.4375 12.2812V10.7188C22.4375 9.85596 21.7378 9.15625 20.875 9.15625Z" fill="#919191"/>
      </svg>
    </div>
    <div class="imgsPreview" v-show="Imgs.length > 0">
      <button type="button" class="clearButton" @click="reset">
        {{ clearAll ? clearAll : "clear All" }}
      </button>
      <div class="imageHolder" v-for="(img, i) in Imgs" :key="i">
        <img :src="img" />
        <span class="delete" style="color: white" @click="deleteImg(--i)">
          <svg width="17" height="19" viewBox="0 0 17 19" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M15.5712 1.35243H11.3439L11.0127 0.693665C10.9426 0.552829 10.8345 0.434361 10.7007 0.351588C10.5669 0.268815 10.4127 0.225022 10.2553 0.225134H6.22879C6.07181 0.224531 5.91783 0.268161 5.7845 0.351026C5.65117 0.433891 5.54387 0.552639 5.47491 0.693665L5.14377 1.35243H0.916429C0.766941 1.35243 0.623575 1.41181 0.517871 1.51751C0.412167 1.62322 0.352783 1.76658 0.352783 1.91607L0.352783 3.04336C0.352783 3.19285 0.412167 3.33622 0.517871 3.44192C0.623575 3.54763 0.766941 3.60701 0.916429 3.60701H15.5712C15.7207 3.60701 15.8641 3.54763 15.9698 3.44192C16.0755 3.33622 16.1349 3.19285 16.1349 3.04336V1.91607C16.1349 1.76658 16.0755 1.62322 15.9698 1.51751C15.8641 1.41181 15.7207 1.35243 15.5712 1.35243V1.35243ZM2.22691 16.6765C2.25379 17.1058 2.44326 17.5088 2.75675 17.8033C3.07024 18.0978 3.48419 18.2617 3.91432 18.2618H12.5733C13.0035 18.2617 13.4174 18.0978 13.7309 17.8033C14.0444 17.5088 14.2339 17.1058 14.2607 16.6765L15.0076 4.7343H1.48007L2.22691 16.6765Z" fill="#CDCDCD"/>
          </svg>
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped> 
.container { 
  width: 100%; 
  position: relative; 
  padding: 0; 
  display: flex; 
  flex-wrap: wrap; 
} 
.drop { 
  width: 100%; 
  height: 100%; 
  top: 0; 
  border-radius: 10px; 
  position: absolute; 
  background-color: #f4f6ff; 
  left: 0; 
  border: 3px dashed #a3a8b1; 
} 
.error { 
  text-align: center; 
  color: red; 
  font-size: 15px; 
} 
.beforeUpload { 
  position: relative; 
  margin-top: 7px; 
  display: flex; 
  align-items: center; 
  justify-content: center; 
  width: 100%; 
  height: 50px; 
  background: #FAFAFA; 
  border-radius: 6.25px; 
} 
@media (min-width: 1024px) { 
  .beforeUpload { 
    width: 120px; 
    height: 120px; 
  } 
} 
.beforeUpload input { 
  width: 100%; 
  margin: auto; 
  height: 100%; 
  opacity: 0; 
  position: absolute; 
  background: red; 
  display: block; 
} 
.beforeUpload input:hover { 
  cursor: pointer; 
} 
.beforeUpload .icon { 
  width: 150px; 
  margin: auto; 
  display: block; 
} 
.imgsPreview { 
    margin-top: 15px; 
}  
@media (min-width: 1024px) { 
  .imgsPreview { 
    margin-top: 0; 
    margin-left: 15px; 
  }  
} 
.imgsPreview .imageHolder { 
  width: 110px; 
  height: 110px; 
  background: #FAFAFA; 
  position: relative; 
  border-radius: 6.93718px; 
  margin: 5px 5px 5px 14px; 
  display: inline-block; 
} 
.imgsPreview .imageHolder:-child { 
  margin: 5px 5px 5px 0px; 
} 
@media (min-width: 1024px) { 
  .imgsPreview .imageHolder { 
    width: 122.74px; 
    height: 122.74px; 
  } 
} 
.imgsPreview .imageHolder img { 
  position: absolute; 
  object-fit: cover; 
  width: 80%; 
  left: 15px; 
  height: 100%; 
} 
.imgsPreview .imageHolder .delete { 
  position: absolute; 
  display: flex; 
  align-items: center; 
  justify-content: center; 
  top: -16px; 
  right: -13px; 
  width: 34.69px; 
  height: 34.69px; 
  background: #FFFFFF; 
  box-shadow: 0px 6.93718px 20.8115px rgba(0, 0, 0, 0.1); 
  border-radius: 48.5602px; 
} 
.imgsPreview .imageHolder .delete:hover { 
  cursor: pointer; 
} 
.imgsPreview .imageHolder .delete .icon { 
  width: 66%; 
  height: 66%; 
  display: block; 
  margin: 4px auto; 
} 
.imgsPreview .imageHolder .plus { 
  color: #2d3748; 
  background: #f7fafc; 
  border-radius: 50%; 
  font-size: 21pt; 
  height: 30px; 
  width: 30px; 
  text-align: center; 
  border: 1px dashed; 
  line-height: 23px; 
  position: absolute; 
  right: -42px; 
  bottom: 43%; 
} 
.plus:hover { 
  cursor: pointer; 
} 
.clearButton { 
  display: none;
  color: #2d3748; 
  position: absolute; 
  top: 7px; 
  right: 7px; 
  background: none; 
  border: none; 
  cursor: pointer; 
} 
</style>
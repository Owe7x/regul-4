<template>
    <div class="container">
        <div class="container-block">
            <div class="large-12 medium-12 small-12 cell">
                <label>
                    <input type="file" id="files" ref="files" accept="image/*" multiple v-on:change="handleFilesUpload()"/>
                </label>
            </div>
            <div class="large-12 medium-12 small-12 cell clear">
                <button v-on:click="addFiles()" class="add">&#10010;</button>
            </div>
            <div class="large-12 medium-12 small-12 cell">
                <div class="grid-x">
                    <div v-for="(file, key) in files" class="large-4 medium-4 small-6 cell file-listing">
                        <span class="remove-file" v-on:click="removeFile( key )"><img src="../assets/delete.svg" alt="" class="delete"></span>
                        <img class="preview" v-bind:ref="'image'+parseInt( key )"/>
                    </div>
                </div>
            </div>
            <br>
        </div>
    </div>
</template>

<script>
  export default {
    data(){
      return {
        files: []
      }
    },
    methods: {
      addFiles(){
        this.$refs.files.click();
      },
      submitFiles(){
        
      },
      handleFilesUpload(){
        let uploadedFiles = this.$refs.files.files;
        for( var i = 0; i < uploadedFiles.length; i++ ){
          this.files.push( uploadedFiles[i] );
        }
        this.getImagePreviews();
      },
      getImagePreviews(){
        for( let i = 0; i < this.files.length; i++ ){
          if ( /\.(jpe?g|png|gif)$/i.test( this.files[i].name ) ) {
            let reader = new FileReader();
            reader.addEventListener("load", function(){
              this.$refs['image'+parseInt( i )][0].src = reader.result;
            }.bind(this), false);
            reader.readAsDataURL( this.files[i] );
          }
        }
      },
      removeFile( key ) {
        this.files.splice( key, 1 );
    }
    }
  }
</script>

<style >
input[type="file"]{
    position: absolute;
    top: -500px;
}
.grid-x {
    display: flex;
    flex-flow: row wrap;
    
}
.preview {
    width: 80px;
    height: 80px;
    border-radius: 6px;
    margin-bottom: 8px;
    margin-right: 8px;
    display: table-cell;
}
.container {
  margin-bottom: 30px;
}
.container-block {
    box-sizing: border-box;
    display: flex;
    padding: 0px 32px;
}
.add {
    display: table-cell;
    float: left;
    width: 80px;
    height: 80px;
    background: #F3F4F6;
    border: 1px solid #EAECF0;
    box-sizing: border-box;
    border-radius: 6px;
}

.remove-file {
  position: absolute;
}

.delete {
  width: 32px;
  height: 32px;
}




@media screen and  (max-width: 550px) {
  .container-block {
    padding: 0px 16px;
  }
    
}

</style>
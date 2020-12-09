<template>
  <div class="hello">
    <button @click="show = !show" class="main-button">Оставить отзыв</button>
    <div class="alert" v-if='active'>
      Спасибо, отзыв опубликован!
    </div>
    <div class="feedback" v-if="show">
      <div class="feedback-top-line">
        <div class="feedback-top-line_h1">
          Мой отзыв
        </div>
        <div class="feedback-top-line_close" @click="show = !show">
          <img src="../assets/close.svg" alt="">
        </div>
      </div>
      <div class="feedback-second-line">
        <div class="feedback-second-line_img">
          <img src="../assets/photo.svg" alt="">
        </div>
        <div class="feedback-second-line_text">
          <div class="name">
            Фоточки в свадебном платьице
          </div>
          <div class="author">
            Алена Смирнова
          </div>
        </div>
      </div>
      <div class="feedback-rating">
        <Rating/>
      </div>
      <div class="feedback-form">
        <form @submit="checkForm" method="post">
          <textarea name="comment" placeholder="Комментарий" v-model="name"></textarea>
          <p>12/500</p>
          <p v-if="errors.length">
            <b>Пожалуйста оставьте комментарий</b>
          </p>
          <p>
            <button type="submit" class="submit">Отправить</button>

          </p>
        </form>
      </div>
      <div class="feedback-img">
            <Img/>
      </div>
      <div class="feedback-next">
        <button @click="next = !next, show = !show" > Продолжить</button>
      </div>
    </div>
    <div class="modal-mobile" v-show="next" >
      <div class="feedback-top-line">
        <div class="feedback-top-line_back">
          <button @click="show = !show, next = !next"><img src="../assets/back.svg" alt=""></button>

        </div>
        <div class="feedback-top-line_h1">
          Мой отзыв
        </div>
        <div class="feedback-top-line_close" @click="next = !next">
          <img src="../assets/close.svg" alt="">
        </div>
      </div>
      <div class="feedback-form-mobile">
        <form @submit="checkForm" method="post">
            <textarea name="comment" placeholder="Комментарий" v-model="name"></textarea>
            <p>12/500</p>
            <p v-if="errors.length">
              <b>Пожалуйста оставьте комментарий</b>
            </p>
            <p>
              <button type="submit" class="submit-mobile" @click="next = !next">Отправить</button>
            </p>
        </form>
      </div>
      <div class="feedback-img-mobile">
            <Img/>
      </div>
    </div>
  </div>
</template>

<script>
import Rating from './Rating.vue'
import Img from './Img.vue'

export default {
  name: 'HelloWorld',
  components: {
    Rating,
    Img
  },
  data () {
    return {
      show: false,
      errors: [],
      name: null,
      active: false,
      next: false
    }
  },
  methods:{
    checkForm:function(e) {
      if(this.name) {
        e.preventDefault();
        this.openItem()
      }
      this.errors = [];
      if(!this.name) this.errors.push("");
      e.preventDefault();
    },
    openItem() {
      this.active = !this.active
      setTimeout(() => {
        this.active = false
      }, 3000)
    }
  },
  mounted () {
      this.openItem
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600&display=swap')

.hello
  padding: 20px 0px
.main-button
  width: 200px
  height: 55px
  border: none
  background: #53C6D1
  border-radius: 6px
  font-family: 'Montserrat', sans-serif
  font-style: normal
  font-weight: 600
  font-size: 14px
  line-height: 20px
  color: #FFFFFF
  padding: 0px
.feedback
  position: relative
  border-radius: 16px 16px 0px 0px
  background-color: #FFFFFF
  max-width: 560px
  padding-bottom: 20px
  margin: 55px auto 0px
  overflow: auto
.feedback-top-line
  display: flex
  justify-content: space-between
  align-items: center
  padding: 16px 21px 16px 32px
  border-bottom: 1px solid #EAECF0
  &_h1
    font-family: 'Montserrat', sans-serif
    font-weight: 600
    font-size: 16px
    line-height: 24px
    color: #3C3C3C
  &_close
    cursor: pointer
.feedback-second-line
  display: flex
  align-items: center
  padding: 24px 0px 0px 32px
  &_img
    margin-right: 20px
    img
      border-radius: 5px
  &_text
    .name
        font-family: Montserrat
        font-style: normal
        font-weight: 600
        font-size: 16px
        line-height: 24px
    .author
        float: left
        font-family: Montserrat
        font-style: normal
        font-weight: normal
        font-size: 12px
        line-height: 16px
.feedback-rating
  padding: 32px 32px 20px 32px
.feedback-form
  padding: 0px 32px
  form
    textarea
      width: 100%
      height: 100px
      padding: 12px 0px 0px 12px
      font-family: Montserrat
      font-style: normal
      font-weight: normal
      font-size: 16px
      line-height: 24px
      color: #7F899E
      border: 1px solid #EAECF0
      background-color: #FAFAFA
      border-radius: 6px
    p
      margin: 4px 32px 16px 0px
      text-align: right
      font-family: Montserrat
      font-style: normal
      font-weight: normal
      font-size: 12px
      line-height: 16px
      text-align: right
      color: #7F899E
.feedback-next
  display: none
  button
    float: right
    border: none
    background: #53C6D1
    border-radius: 6px
    font-family: 'Montserrat', sans-serif
    font-style: normal
    font-weight: 600
    font-size: 14px
    line-height: 20px
    color: #FFFFFF
    padding: 6px 12px
    margin-bottom: 16px
.submit
    position: absolute
    right: 32px
    bottom: 0
    border: none
    background: #53C6D1
    border-radius: 6px
    font-family: 'Montserrat', sans-serif
    font-style: normal
    font-weight: 600
    font-size: 14px
    line-height: 20px
    color: #FFFFFF
    padding: 6px 12px
    margin-bottom: 16px
.alert 
  position: absolute
  top: 10px
  right: 0
  width: 279px
  background: #15A758
  box-shadow: 0px 2px 24px rgba(0, 0, 0, 0.08)
  border-radius: 6px
  font-family: Montserrat
  font-style: normal
  font-weight: 500
  font-size: 14px
  line-height: 20px
  padding: 8px 12px
  color: #FFFFFF
.modal-mobile
  position: relative
  border-radius: 16px 16px 0px 0px
  background-color: #FFFFFF
  max-width: 560px
  padding-bottom: 20px
  margin: 55px auto 0px
  overflow: auto
.feedback-top-line
  border: none
  &_back
    button
      background: none
      border: none
.feedback-form-mobile
  padding: 0px 32px 0px 16px
  form
    textarea
      width: 100%
      height: 146px
      padding: 12px 0px 0px 12px
      font-family: Montserrat
      font-style: normal
      font-weight: normal
      font-size: 16px
      line-height: 24px
      color: #7F899E
      border: 1px solid #EAECF0
      background-color: #FAFAFA
      border-radius: 6px
    p
      margin: 4px 32px 16px 0px
      text-align: right
      font-family: Montserrat
      font-style: normal
      font-weight: normal
      font-size: 12px
      line-height: 16px
      text-align: right
      color: #7F899E
.submit-mobile
  position: absolute
  right: 32px
  bottom: 0
  border: none
  background: #53C6D1
  border-radius: 6px
  font-family: 'Montserrat', sans-serif
  font-style: normal
  font-weight: 600
  font-size: 14px
  line-height: 20px
  color: #FFFFFF
  padding: 6px 12px
  margin-bottom: 16px
@media screen and ( max-width: 550px )
  .feedback-top-line 
    border: none
    padding-left: 16px
  .feedback-second-line
    flex-direction: column
    align-items: flex-start
    padding: 16px 0px 0px 16px
    &_img
      margin-bottom: 13px
      img
        border-radius: 5px
    &_text
      .name
          font-family: Montserrat
          font-style: normal
          font-weight: 600
          font-size: 16px
          line-height: 24px
      .author
          float: left
          font-family: Montserrat
          font-style: normal
          font-weight: normal
          font-size: 12px
          line-height: 16px
  .feedback-rating
    padding: 32px 32px 20px 16px
  .feedback-form
    display: none
  .feedback-img 
    display: none
  .submit
      display: none
  .feedback-next
    display: block

</style>

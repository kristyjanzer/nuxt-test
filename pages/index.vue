<template>
  <main>

    <div class="container">
      <div class="wrap">
        <div class="add">
          <div class="add__top">
            <h1 class="add__title">Добавление товара</h1>
            <div class="add__card" @click="showForm">
              <img v-if="!show" src="../assets/img/plus-icon.svg" alt="">
              <img v-else src="../assets/img/minus-icon.svg" alt="">
            </div>
          </div>
          <form @submit.prevent class="add__form" :class="{ 'active': show }">
            <div class="add__box">
              <label class="add__label label">Наименование товара</label>
              <input class="add__text" type="text" placeholder="Введите наименование товара" required v-model="new_title">
            </div>
            <div class="add__box">
              <label class="add__label">Описание товара</label>
              <textarea class="add__text textarea" type="text" placeholder="Введите описание товара" v-model="new_descr"></textarea>
            </div>
            <div class="add__box">
              <label class="add__label label">Ссылка на изображение товара</label>
              <input class="add__text" type="text" placeholder="Введите ссылку" required v-model="new_link">
            </div>
            <div class="add__box">
              <label class="add__label label">Цена товара</label>
              <input class="add__text" type="text" placeholder="Введите цену" required v-model="new_price">
            </div>
            <button class="add__button" :class="{ 'active': disBtn }" type="button" @click="addCard">Добавить товар</button>
          </form>
        </div>
        <div class="cards">
          <Card 
            :item="item" 
            v-for="(item, index) in todoList" 
            :key="index" 
            @delete-card="deleteCard"></Card>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      todoList: [
        {
          id: 1,
          title: "Наименование товара",
          descr: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000
        },
        {
          id: 2,
          title: "Наименование товара",
          descr: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 20000
        },
        {
          id: 3,
          title: "Наименование товара",
          descr: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 30000
        },
        {
          id: 4,
          title: "Наименование товара",
          descr: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 40000
        },
        {
          id: 5,
          title: "Наименование товара",
          descr: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 50000
        },
        {
          id: 6,
          title: "Наименование товара",
          descr: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 60000
        },
      ],
      new_title: '',
      new_link: '',
      new_descr: '',
      new_price: '',
      show: false,
    };
  },
  computed: {
    disBtn() {
      if (this.new_title !== '' && this.new_link !== '' && this.new_price !== '') return true; 
      return false;
    },
  },
  methods: {
    addCard() {
      if (this.new_title && this.new_link && this.new_price) {
        this.todoList.unshift({
          id: this.todoList.length,
          title: this.new_title,
          descr: this.new_descr,
          link: this.new_link,
          price: this.new_price,
        });
      }
      this.new_title = '',
      this.new_descr = '',
      this.new_link = '',
      this.new_price = '';
      return true;
    },
    deleteCard(id) {
      this.todoList = this.todoList.filter(e => e.id !== id)
    },
    showForm() {
      this.show = !this.show;
    },
  },
}
</script>


<style lang="sass">
  *
    margin: 0
    padding: 0
    box-sizing: border-box
    font-family: 'Source Sans Pro', sans-serif

  body
    background: rgba(255, 254, 251, 0.8)
    color: #000

  button
    background: transparent
    border: none
    cursor: pointer
    padding: 0
    margin: 0
    outline: none

  .container
    max-width: 1440px
    margin: 0 auto
    padding: 0 32px
    width: 100%

  .wrap
    display: flex
    align-items: flex-start
    margin: 32px 0

  .cards
    margin-top: 43px
    display: flex
    gap: 16px
    flex-wrap: wrap
    justify-content: space-evenly
  
  .add
    max-width: 332px
    width: 100%
    margin-right: 16px
    &__top
      display: flex
      align-items: center
      justify-content: space-evenly
      max-width: 400px
      margin: 0 auto
    &__card
      display: none
    &__box
      font-size: 0
      &:not(:first-child)
        margin-top: 16px
    &__title
      font-family: Source Sans Pro
      font-style: normal
      font-weight: 600
      font-size: 28px
      line-height: 35px
      color: #3F3F3F
    &__form
      min-width: 255px
      min-height: 440px
      padding: 24px
      background: #FFFEFB
      box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
      border-radius: 4px
      margin-top: 16px
    &__label
      font-size: 10px
      line-height: 13px
      letter-spacing: -0.02em
      color: #49485E
    &__text
      width: 100%
      min-height: 36px
      background: #FFFEFB
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
      border-radius: 4px
      padding: 10px 16px
      border: 1px solid transparent
      outline: none
      margin-top: 4px
      font-size: 12px
      line-height: 15px
      color: #000
      transition: all .5s ease
      &:focus
        border: 1px solid #ccc
      &:focus:required:invalid
        border-color: red
    &__button
      background: #EEEEEE
      border-radius: 10px
      width: 100%
      display: block
      min-height: 36px
      font-weight: 600
      font-size: 12px
      line-height: 15px
      text-align: center
      letter-spacing: -0.02em
      color: #B4B4B4
      margin-top: 24px
      font-family: 'Inter', sans-serif
      pointer-events: none
      &.active
        background: #7BAE73
        color: #FFFFFF
        pointer-events: visible
  .label
    position: relative
    &::after
      position: absolute
      content: ''
      background: #FF8484
      border-radius: 50%
      width: 4px
      height: 4px
      top: 0
      right: -5px
  .textarea
     resize: none
     min-height: 108px

  @keyframes show
    0%
      transform: translateX(-150%)
    100%
      transform: translateY(0)

  @media(max-width: 854px)
    .container
      padding: 0 15px
    .wrap
      flex-direction: column
    .cards
      margin-top: 25px
    .add
      max-width: 100%
      margin-right: 0
      &__title
        font-size: 23px
        text-align: center
        cursor: pointer
      &__form
        display: none
        &.active
          display: block
          animation: show 1s ease
      &__card
        display: block
        width: 20px
        height: 20px

</style>
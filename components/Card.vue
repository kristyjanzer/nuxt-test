<template>

    <div class="card">
      <img class="card__image" src="../assets/img/card.jpg" alt="">
      <div class="card__box">
        <div class="card__title">{{ item.title }}</div>
        <div class="card__descr">{{ item.descr }}</div>
        <div class="card__price"><span class="price">{{ item.price }}</span> руб.</div>
      </div>
      <span class="delete" @click="$emit('delete-card', item.id)"></span>
    </div>

</template>

<script>
  export default {
    props: ['item'],
  }
</script>

<style lang="sass" scoped>
  .card
    max-width: 332px
    min-height: 423px
    background: #FFFEFB
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
    border-radius: 4px
    display: flex
    flex-direction: column
    position: relative
    transition: all .5s ease
    .delete
      position: absolute
      top: 0
      right: 0
      transform: translateY(-50%)
      cursor: pointer
      opacity: 0
      width: 0
      transition: all ease-in 0.25s
      &::after
        position: absolute
        content: ''
        width: 32px
        height: 32px
        top: 50%
        right: -25px
        background-image: url('../assets/img/delete-icon.svg')
        background-repeat: no-repeat
        background-position: center
        background-size: contain
        transform: translate(-50%, -50%) scale(0.5)
        transition: all ease-in 0.25s
    &:hover
      cursor: pointer
      box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.1), 0px 6px 10px rgba(0, 0, 0, 0.1)
    &:hover .delete
      width: 44px
      opacity: 1
      &::after
        transform: translate(-50%, -50%) scale(1)
    &__image
      display: block
      max-width: 100%
    &__box
      padding: 16px
      height: 100%
      display: flex
      flex-direction: column
    &__title
      font-weight: 600
      font-size: 20px
      line-height: 25px
      color: #3F3F3F
    &__descr
      margin-top: 16px
      font-weight: normal
      font-size: 16px
      line-height: 20px
      color: #3F3F3F
      flex: 1 1 auto
    &__price
      font-weight: 600
      font-size: 24px
      line-height: 30px
      color: #3F3F3F
      margin-top: 10px

  @media(max-width: 1091px)
    .card
      max-width: 250px 
  @media(max-width: 854px)
    .card
      max-width: 332px

</style>
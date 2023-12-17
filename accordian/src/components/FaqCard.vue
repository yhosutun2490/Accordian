<template>
  <div class="card-container">
    <div class="title-wrap">
      <img class="title-img" :src="StarIcon" alt="star-icon"/>
      <p class="title-word">FAQ</p>
    </div>
    <div class="card-row-wrap">
      <div class="card-row" v-for="data in cardRowData" :key="data.id">
        <div class="row-title-wrap">
          <div>{{ data.title }}</div>
          <button class="open-btn" v-if="data.isShowCard" @click.stop ="toggleCard(data.id)"></button>
          <button class="close-btn" v-if="!data.isShowCard" @click.stop="toggleCard(data.id)"></button>
        </div>
        <div class="card-content" v-show="data.isShowCard">
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Et fugit cupiditate unde veniam minus sequi, vitae aperiam quibusdam provident similique eligendi consequatur, impedit deleniti modi adipisci necessitatibus quos dolores. Nam!</p>
        </div>
      </div>
    </div>

  </div>

</template>
<script setup>
import StarIcon from "../assets/images/icon-star.svg"
import {ref} from 'vue'
const cardRowData = ref([
  {
    id: 1,
    title: 'What is Frontend Mentor, and how will it help me?',
    content: 'hello',
    isShowCard: false,
  },
   {
    id: 2,
    title: 'What is Frontend Mentor, and how will it help me?',
    content: 'hello',
     isShowCard: false,
  },
   {
    id: 3,
    title: 'What is Frontend Mentor, and how will it help me?',
    content: 'hello',
     isShowCard: false,
  },
])

function toggleCard (id) {
  cardRowData.value = cardRowData.value.map(item=>{
    if (item.id === id ) {
      item.isShowCard =  !item.isShowCard
    }  return item
  })
}
</script>
<style scoped lang="scss">
.card-container {
  width: 41.66%;
  background-color: white;
  border-radius: 16px;
}
.title-wrap {
  display: flex;
  align-items: center;
  height: 66px;
  .title-img {
    width: 40px;
    height: 40px;
    margin-right: 24px;
  }
  .title-word {
    font-family: 'Work Sans';
    font-style: normal;
    font-weight: 700;
    font-size: 56px;
    line-height: 66px;
    color: #301534;
  }
}
.card-row:not(:last-child) { 
    border-bottom: 1px solid #F8EEFF;
  } 
.row-title-wrap {
  width: 100%;
  display: flex;
  align-items: center;
  height: 30px;
  padding: 24px 0;
  
  
  .open-btn,.close-btn {
    all: unset;
    margin-left: auto;
    width: 24px;
    height: 24px;
    cursor: pointer;
  }
  .open-btn {
    background-image: url(../assets/images/icon-plus.svg);
    background-position: center;
    background-size: contain;
  }
  .close-btn {
    background-image: url(../assets/images/icon-minus.svg);
    background-position: center;
    background-size: contain;
  }
}

</style>
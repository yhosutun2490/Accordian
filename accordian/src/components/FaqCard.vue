<template>
  <div class="card-container">
    <div class="title-wrap">
      <img class="title-img" :src="StarIcon" alt="star-icon"/>
      <p class="title-word">FAQs</p>
    </div>
    <div class="card-row-wrap">
      <div class="card-row" v-for="data in cardRowData" :key="data.id">
        <div class="row-title-wrap">
          <div class="row-title-word">{{ data.title }}</div>
          <button class="open-btn" v-if="!data.isShowCard" @click.stop ="toggleCard(data.id)"></button>
          <button class="close-btn" v-if="data.isShowCard" @click.stop="toggleCard(data.id)"></button>
        </div>
        <div class="card-content" v-show="data.isShowCard">
          <p>{{ data.content }}</p>
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
    content: 'Frontend Mentor offers realistic coding challenges to help developers improve their frontend coding skills with projects in HTML, CSS, and JavaScript. It’s suitable for all levels and ideal for portfolio building.',
    isShowCard: false,
  },
   {
    id: 2,
    title: 'Is Frontend Mentor free?',
    content: 'Frontend Mentor offers realistic coding challenges to help developers improve their frontend coding skills with projects in HTML, CSS, and JavaScript. It’s suitable for all levels and ideal for portfolio building.',
     isShowCard: false,
  },
   {
    id: 3,
    title: 'Can I use Frontend Mentor projects in my portfolio?',
    content: 'Frontend Mentor offers realistic coding challenges to help developers improve their frontend coding skills with projects in HTML, CSS, and JavaScript. It’s suitable for all levels and ideal for portfolio building.',
     isShowCard: false,
  },
   {
    id: 4,
    title: "How can I get help if I'm stuck on a challenge?",
    content: 'Frontend Mentor offers realistic coding challenges to help developers improve their frontend coding skills with projects in HTML, CSS, and JavaScript. It’s suitable for all levels and ideal for portfolio building.',
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
  padding: 40px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  min-height: 335px;  
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
    font-size: 56px;
    font-weight: 700;
    text-align: start;
  }
}
.card-row:not(:last-child) { 
    border-bottom: 1px solid #F8EEFF;
  } 
.card-content {
  color: #8B6990;
  text-align: start;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px;  
}
.row-title-wrap {
  width: 100%;
  display: flex;
  align-items: center;
  height: 30px;
  padding: 24px 0;
  .row-title-word {
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    line-height: normal;
    width: 85% ;
    text-align: start;
    &:hover {
      color: #AD28EB;
      cursor: pointer;
    }
  }
  
  .open-btn,.close-btn {
    all: unset;
    margin-left: auto;
    width: 30px;
    height: 30px;
    cursor: pointer;
  }
  .open-btn {
    background-image: url(../assets/images/icon-plus.svg);
  }
  .close-btn {
    background-image: url(../assets/images/icon-minus.svg);
  }
}
@media screen and (max-width: 576px) {
  .card-container {
    width: 75%;
    max-width: 100dvw;
    height: 65%;
  }
}
@media screen and (max-width: 376px) {
  .card-container {
    max-width: 87.2%;
    top: 17.2%;
    left: 50%;
    transform: translate(-50%,0%);
    height: auto;
  }
}

</style>
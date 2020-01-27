<template>
  <div class="main_wrapper">
    <div class="header_wrapper">
      <div class="header">
        <div class="header_img">
          <img src="avatar.png" alt="">
        </div>
        <div class="header_text">
          <p class="header_title">Вероника Ростова</p>
          <p class="header_subtitle">Менеджер по продажам</p>
          <div class="header_description">Подберу для вас самые лучшие предложения. <br> Мои услуги абсолютны</div>
        </div>
      </div>
    </div>
    <div class="services">
      <div class="services_head">Услуг</div>
      <div class="services_items">
        <div 
          class="services_item"
          
          v-for="(item, index) in servicesList" :key="index"
        >
          <div 
            :class="item.color"
            :style="'width: '+ computedWidth(item.count)"
            :width="(100 / item.count) + '%'" 
            class="item_text"
          >{{ item.text }}</div>
          <div class="item_count">{{ item.count }}</div>
        </div>
      </div>
      <div class="services_total">
        <p>Всего</p>
        <p class="total">15</p>
      </div>
    </div>
    <div class="reviews">
      <div class="reviews_head">
        <div class="reviews_head_text">
          <p class="title">Последние отзывы </p>
          <a href="#">Все отзывы</a>
        </div>
        <div class="reviews_head_stats">
          <div class="stats_item"><img src="like.png" alt=""><span>131</span></div>
          <div class="stats_item"><img src="comment.png" alt=""><span>14</span></div> 
        </div>
      </div>
      <div class="reviews_items">
        <div 
          class="reviews_item"
          v-for="(item, index) in reviews" :key="index"
        >
          <div class="item_head">
            <p class="name">{{ item.name }}</p>
            <span class="date">{{ item.date }}</span>
          </div>
          <div class="item_text">{{ item.text }}</div>
        </div>
      </div>
    </div>
    <div class="add_review">
      <textarea v-model="newReview" rows='4'></textarea>
      <button @click="addReview">Написать консультанту</button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    newReview: '',
    reviews: [
      {
        name: 'Самуил',
        date: '13 октября 2011',
        text: 'Привет, Верунь! ниче себе ты крутая. фотка класс!!!! ',
      },
      {
        name: 'Лилия Семёновна',
        date: '14 октября 2011',
        text: 'Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент, это и есть всемирно известный центр огранки алмазов и торговли бриллиантами?',
      },
      {
        name: 'Лилия Семёновна',
        date: '14 октября 2011',
        text: 'Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?',
      },
    ],
    servicesList: [
      {
        text: 'Ручное бронирование',
        count: '11',
        color: 'green',
      },
      {
        text: 'Пакетные туры',
        count: '3',
        color: 'blue',
      },
      {
        text: 'Отели',
        count: '1',
        color: 'blue',
      },
    ]
  }),
  
  methods: {
    addReview() {
      let review = {
        name: 'Анонимно',
        date: '26 января 2020',
        text: this.newReview
      }
      this.reviews.push(review)
      this.newReview = ''
    },
    computedWidth(c) {
      return ((Number(c) / 15) * 100) + '%'
    }
  },
  
}
</script>

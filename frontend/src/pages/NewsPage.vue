<template>
  <div>
    <side-bar></side-bar>
    <div class="wrap">
      <h1>5월 마지막주 영화 예매 순위</h1>
      <ul class="news">
        <li v-for="newss in news" class="item" v-bind:key="newss">
          <span class="rank">{{newss.id}}</span>
          <router-link :to="{ name: 'show', params: { id: newss.id }}">
            <img v-bind:src="newss.poster" class="poster">
          </router-link>
          <div class="detail">
            <strong class="tit">{{newss.name}}</strong>
            <span class="rate">예매율 <span class="num">{{newss.rate}}</span></span>
            <router-link :to="{ name: 'show', params: { id: newss.id }}" class="link">자세히보기</router-link>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
  import SideBar from '../components/SideBar.vue'
  export default {
    components: {
      SideBar
    },
    name: 'NewsPage',
    created() {
      // 컴포넌트가 생성될 때, /api/newsss에 요청을 보냅니다.          
      this.$http.get('/api/news')
        .then((response) => {
          this.news = response.data
        })
    },
    data() {
      return {
        news: []
      }
    }
  }
</script>
<style>
</style>
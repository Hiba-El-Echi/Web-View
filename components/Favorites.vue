<template>
  <div class="container">
    <div class="text-container">
      <span class="favoris">
        Liste des numéros favoris
      </span>
      <br />
      <span class="number">
        <span class="num">4/5</span>
        numéros favoris
      </span>
    </div>
    <div class="search-container">
      <van-search v-model="value" placeholder="Identifiant" />
    </div>
    <div class="favorites-list" v-for="favorite in favorites" :key="favorite">
      <div class="favorite-list-item">
        <img src="./../assets/img/contact.svg" />
        <div class="item-element">
          <span>{{ favorite.name }}</span> <br>
          <span>{{ favorite.number }}</span>
        </div>
      </div>
      <hr>
    </div>
  </div>
</template>
<script setup>
let value = ref('')
let favorites = ref([
  { name: 'Maman', number: '5656726768' },
  { name: 'Travail', number: '565676636768' },
  { name: 'Maison', number: '544676636768' },
])
</script>

<style lang="scss" scoped>
.container {
  margin: 20px;
  .text-container {
    .favoris {
      color: #000;
      font-size: 14px;
      font-weight: 500;
      line-height: normal;
    }
    .number {
      color: #999;
      font-size: 12px;
      font-weight: 400;
      line-height: normal;
      .num {
        color: #ff7900;
        font-size: 12px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
      }
    }
  }

  .search-container {
    margin-top: 10px;
  }

  .favorites-list {
    .favorite-list-item {
      display: flex;
      gap: 20px;
      align-items: center;
      height: 56px;
      .item-element{
      
      }
    }
  }
}
</style>

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
      <van-swipe-cell>
        <div class="favorite-list-item">
          <img src="./../assets/img/contact.svg" />
          <div class="item-element">
            <span class="name">{{ favorite.name }}</span>
            <br />
            <span class="number">{{ favorite.number }}</span>
          </div>
        </div>
        <template #right>
          <img src="./../assets/img/delete.svg" />
          <!-- <van-button
            square
            text="Delete"
            type="danger"
            class="delete-button"
          /> -->
        </template>

        <hr />
      </van-swipe-cell>
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
      .item-element {
        .name {
          color: #000;

          font-size: 14px;
          font-style: normal;
          font-weight: 500;
          line-height: normal;
          letter-spacing: 0.563px;
        }
        .number {
          color: #000;
          font-size: 12px;
          font-style: normal;
          font-weight: 400;
          line-height: normal;
          letter-spacing: 0.25px;
        }
      }
    }
  }
}
</style>

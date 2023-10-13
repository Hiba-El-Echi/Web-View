<template>
  <div class="container">
    <div class="text-container">
      <span class="favoris">
        Liste des numéros favoris
      </span>
      <br />
      <span class="number">
        <span class="num">{{ favorites.length }} /5</span>
        numéros favoris
      </span>
    </div>
    <div class="search-container">
      <van-search v-model="value" placeholder="Identifiant" />
    </div>
    <div
      class="favorites-list"
      v-for="favorite in favorites"
      :key="favorite.id"
    >
      <van-swipe-cell :right-width="80">
        <template #left>
          <div class="modif-img">
            <img src="./../assets/img/modif.svg" />
          </div>
        </template>
        <div class="favorite-list-item">
          <img src="./../assets/img/contact.svg" />
          <div class="item-element">
            <span class="name">{{ favorite.name }}</span>
            <br />
            <span class="number">{{ favorite.number }}</span>
          </div>
        </div>
        <template #right>
          <div class="delete-img" @click="deleteFavorite(favorite.id)">
            <img src="./../assets/img/delete.svg" />
          </div>
        </template>
      </van-swipe-cell>
      <hr class="line" />
    </div>
  </div>
</template>
<script setup>
let value = ref('')
let favorites = ref([
  { id: '1', name: 'Maman', number: '5656726768' },
  { id: '2', name: 'Travail', number: '565676636768' },
  { id: '3', name: 'Maison', number: '544676636768' },
])

const deleteFavorite = (favoriteId) => {
  const index = favorites.value.findIndex(
    (favorite) => favorite.id === favoriteId,
  )
  if (index !== -1) {
    favorites.value.splice(index, 1)
  }
}
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
    .line {
      margin: 0px;
    }
    .favorite-list-item {
      display: flex;
      gap: 20px;
      align-items: center;
      height: 65px;
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
    .delete-img {
      background-color: #000;
      height: 100%;
      width: 80px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .modif-img {
      background-color: #f16e00;
      height: 100%;
      width: 80px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>

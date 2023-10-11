<template>
  <div class="header">
     <div class="arrow">
       <nuxt-link>
         <img src="./../assets/img/back-icon.svg" />
       </nuxt-link>
     </div>
     <div>
       <span class="text-num">Numéros Favoris</span>
     </div>
   </div>
</template>
<style  lang="scss" scoped>
 .header {
   display: flex;
   gap: 10px;
   line-height: 20px;
   margin-top: 30px;
   .arrow {
     align-content: center;
   }
   .text-num {
     color: #000;
     font-size: 18px;
     font-style: normal;
     font-weight: 700;
     line-height: 20px; 
     letter-spacing: 0.25px;
   }
 }
</style>


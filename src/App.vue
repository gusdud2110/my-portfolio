<script setup>
import { portfolioItems } from './data/portfolio'
import PortfolioCard from './components/PortfolioCard.vue'
import Introduction from './components/Introduction.vue'
</script>

<template>
  <main>
    <Introduction />

    <section class="portfolio">
      <div class="portfolio__header">
        <h2 class="portfolio__title">PROJECT</h2>
      </div>

      <div class="portfolio__grid">
        <PortfolioCard
          v-for="(item, index) in portfolioItems"
          :key="index"
          :item="item"
        />
      </div>
    </section>
  </main>
</template>

<style scoped>
.portfolio {
  padding: 80px 40px 120px;
  background: #f7f8fc;
  min-height: 100vh;
}

.portfolio__header {
  text-align: center;
  margin-bottom: 52px;
}

.portfolio__title {
  font-size: 32px;
  font-weight: 800;
  color: #111;
  letter-spacing: -1px;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

.portfolio__title span {
  font-weight: 400;
  color: #5865f2;
  font-size: 22px;
  margin-left: 6px;
}

.portfolio__desc {
  margin-top: 10px;
  font-size: 14px;
  color: #999;
  letter-spacing: -0.2px;
}

.portfolio__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  max-width: 1200px;
  margin: 0 auto;
}

@media (max-width: 1024px) {
  .portfolio__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .portfolio {
    padding: 60px 20px 80px;
  }

  .portfolio__grid {
    grid-template-columns: 1fr;
  }

  .portfolio__title {
    font-size: 24px;
  }
}
</style>
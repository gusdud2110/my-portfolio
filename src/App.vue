<script setup>
import { nextTick, onMounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'
import { portfolioItems } from './data/portfolio'
import PortfolioCard from './components/PortfolioCard.vue'
import Introduction from './components/Introduction.vue'

onMounted(async () => {
  await nextTick()

  AOS.init({
    duration: 700,
    easing: 'ease-out-cubic',
    once: true,
    offset: 80,
  })
  AOS.refreshHard()
})
</script>

<template>
  <main>
    <Introduction />

    <section class="portfolio">
      <div class="portfolio__header" data-aos="fade-up">
        <h2 class="portfolio__title">PROJECT</h2>
      </div>

      <div class="portfolio__grid">
        <PortfolioCard
          v-for="(item, index) in portfolioItems"
          :key="index"
          :item="item"
          :animation-delay="Math.min(index * 100, 400)"
        />
      </div>
    </section>
  </main>
</template>

<style scoped>
.portfolio {
  padding: 96px 40px 120px;
  background:
    radial-gradient(ellipse at 50% 0, rgba(99, 91, 255, 0.06), transparent 42%),
    #f7f8fc;
  min-height: 100vh;
}

.portfolio__header {
  text-align: center;
  margin-bottom: 56px;
}

.portfolio__header::before {
  content: 'SELECTED WORK';
  display: inline-block;
  margin-bottom: 12px;
  color: #7169e8;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 2.4px;
}

.portfolio__title {
  font-size: clamp(28px, 3vw, 36px);
  font-weight: 800;
  color: #1d2340;
  letter-spacing: -1.4px;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

.portfolio__title span {
  font-weight: 400;
  color: #7169e8;
  font-size: 22px;
  margin-left: 6px;
}

.portfolio__desc {
  margin-top: 10px;
  font-size: 14px;
  color: #81889a;
  letter-spacing: -0.2px;
}

.portfolio__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 28px;
  max-width: 1180px;
  margin: 0 auto;
}

@media (max-width: 1024px) {
  .portfolio__grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .portfolio {
    padding: 72px 20px 88px;
  }

  .portfolio__grid {
    grid-template-columns: 1fr;
  }

  .portfolio__title {
    font-size: 24px;
  }
}
</style>
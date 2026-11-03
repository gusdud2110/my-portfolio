<script setup>
defineProps({
  item: {
    type: Object,
    required: true
  },
  animationDelay: {
    type: Number,
    default: 0
  }
})

const statusColor = (status) => {
  if (status === '운영중') return 'active'
  if (status === '사업종료') return 'closed'
  if (status === '구축중') return 'building'
  return 'default'
}
</script>

<template>
  <article class="card" data-aos="fade-up" :data-aos-delay="animationDelay">
    <!-- Thumbnail -->
    <div class="card__thumb" :class="{ 'no-image': !item.bgImage }">
      <img v-if="item.bgImage" :src="item.bgImage" :alt="item.title" />
      <div v-else class="card__placeholder">
        <span>{{ item.title.charAt(0) }}</span>
      </div>
    </div>

    <!-- Body -->
    <div class="card__body">
      <div class="card__header">
        <div>
          <h3 class="card__title">{{ item.title.trim() }}</h3>
          <p v-if="item.subtitle" class="card__subtitle">{{ item.subtitle }}</p>
        </div>
        <span v-if="item.status" class="card__status" :class="statusColor(item.status)">
          {{ item.status }}
        </span>
      </div>

      <!-- Meta Info -->
      <ul class="card__meta">
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
          {{ item.period }}
        </li>
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
          {{ item.role }}
        </li>
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
          {{ item.device.join(' · ') }}
        </li>
      </ul>

      <!-- Skills -->
      <div class="card__skills">
        <span v-for="skill in item.skills" :key="skill" class="skill-tag">{{ skill }}</span>
      </div>

      <!-- Achievements -->
      <ul v-if="item.achievements && item.achievements.length" class="card__achievements">
        <li v-for="achieve in item.achievements" :key="achieve">{{ achieve }}</li>
      </ul>

      <!-- Link -->
      <a v-if="item.link && item.link !== '#'" :href="item.link" target="_blank" class="card__link">
        바로가기
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="7" y1="17" x2="17" y2="7"/><polyline points="7 7 17 7 17 17"/></svg>
      </a>
    </div>
  </article>
</template>

<style scoped>
.card {
  background: #fff;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 8px 26px rgba(40, 48, 89, 0.07);
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
  border: 1px solid #e9ebf3;
}

.card:hover {
  transform: translateY(-7px);
  box-shadow: 0 18px 38px rgba(40, 48, 89, 0.13);
  border-color: #d9d7ff;
}

/* Thumbnail */
.card__thumb {
  width: 100%;
  height: 190px;
  overflow: hidden;
  background: linear-gradient(135deg, #e8eaff 0%, #f0edff 52%, #e6f4ff 100%);
  flex-shrink: 0;
}

.card__thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  transition: transform 0.6s ease;
}

.card:hover .card__thumb img {
  transform: scale(1.05) translateY(-4%);
}

.card__placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card__placeholder span {
  font-size: 52px;
  font-weight: 700;
  color: rgba(92, 91, 160, 0.22);
  letter-spacing: 0;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

/* Body */
.card__body {
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 18px;
  flex: 1;
}

/* Header */
.card__header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 12px;
}

.card__header > div {
  min-width: 0;
}

.card__title {
  font-size: 18px;
  font-weight: 750;
  color: #202640;
  line-height: 1.4;
  letter-spacing: -0.5px;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

.card__subtitle {
  margin-top: 5px;
  font-size: 12.5px;
  color: #858b9d;
  line-height: 1.5;
  letter-spacing: 0;
}

/* Status Badge */
.card__status {
  flex-shrink: 0;
  font-size: 10.5px;
  font-weight: 650;
  padding: 5px 10px;
  border-radius: 8px;
  letter-spacing: 0;
  white-space: nowrap;
  margin-top: 1px;
}

.card__status.active {
  background: #e6f7f1;
  color: #258568;
}

.card__status.building {
  background: #fff4e0;
  color: #a56b13;
}

.card__status.closed {
  background: #f0f0f0;
  color: #858b9d;
}

.card__status.default {
  background: #eef2ff;
  color: #625bd4;
}

/* Meta */
.card__meta {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin: 0;
  padding: 14px 15px;
  border: 1px solid #eef0f6;
  border-radius: 12px;
  background: #fafbfe;
  list-style: none;
}

.card__meta li {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 12px;
  color: #626a7d;
  line-height: 1.5;
  letter-spacing: 0;
}

.card__meta li svg {
  box-sizing: content-box;
  width: 15px;
  height: 15px;
  padding: 5px;
  flex-shrink: 0;
  color: #7169d5;
  background: #efefff;
  border-radius: 8px;
}

/* Skills */
.card__skills {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
}

.skill-tag {
  font-size: 10.5px;
  font-weight: 550;
  color: #5e59ad;
  background: #f4f3ff;
  border: 1px solid #ebeaff;
  padding: 4px 9px;
  border-radius: 6px;
  letter-spacing: 0;
  line-height: 1.4;
}

/* Achievements */
.card__achievements {
  display: flex;
  flex-direction: column;
  gap: 7px;
  margin: 0;
  padding: 15px 16px;
  border-top: 1px solid #edf0f5;
  border-radius: 12px;
  background: #fff;
  list-style: none;
}

.card__achievements li {
  font-size: 12px;
  color: #687084;
  padding-left: 12px;
  position: relative;
  line-height: 1.55;
  letter-spacing: 0;
}

.card__achievements li::before {
  content: '';
  position: absolute;
  left: 1px;
  top: 0.62em;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: #aaa5e8;
}

/* Link */
.card__link {
  display: inline-flex;
  align-items: center;
  align-self: flex-start;
  gap: 7px;
  font-size: 12px;
  font-weight: 650;
  color: #625bd4;
  margin-top: auto;
  padding: 8px 11px;
  border-radius: 8px;
  background: #f4f3ff;
  transition: gap 0.2s ease, background 0.2s ease, color 0.2s ease;
}

.card__link:hover {
  gap: 10px;
  color: #4c45b7;
  background: #ecebff;
}

.card__link svg {
  width: 13px;
  height: 13px;
}

@media (max-width: 640px) {
  .card__body {
    padding: 20px;
    gap: 16px;
  }
}
</style>

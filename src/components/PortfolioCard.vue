<script setup>
defineProps({
  item: {
    type: Object,
    required: true
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
  <article class="card">
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
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0,0,0,0.07);
  display: flex;
  flex-direction: column;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  border: 1px solid #f0f0f0;
}

.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 32px rgba(0,0,0,0.13);
}

/* Thumbnail */
.card__thumb {
  width: 100%;
  height: 180px;
  overflow: hidden;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  flex-shrink: 0;
}

.card__thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top;
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
  color: rgba(255,255,255,0.15);
  letter-spacing: 0;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

/* Body */
.card__body {
  padding: 20px 22px 22px;
  display: flex;
  flex-direction: column;
  gap: 14px;
  flex: 1;
}

/* Header */
.card__header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 10px;
}

.card__title {
  font-size: 17px;
  font-weight: 700;
  color: #111;
  line-height: 1.3;
  letter-spacing: -0.4px;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

.card__subtitle {
  margin-top: 3px;
  font-size: 12px;
  color: #888;
  line-height: 1.4;
  letter-spacing: -0.2px;
}

/* Status Badge */
.card__status {
  flex-shrink: 0;
  font-size: 11px;
  font-weight: 600;
  padding: 3px 9px;
  border-radius: 20px;
  letter-spacing: 0;
  white-space: nowrap;
  margin-top: 2px;
}

.card__status.active {
  background: #e6f7f1;
  color: #0a8a5a;
}

.card__status.building {
  background: #fff4e0;
  color: #c07000;
}

.card__status.closed {
  background: #f0f0f0;
  color: #888;
}

.card__status.default {
  background: #eef2ff;
  color: #5865f2;
}

/* Meta */
.card__meta {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.card__meta li {
  display: flex;
  align-items: center;
  gap: 7px;
  font-size: 12.5px;
  color: #555;
  line-height: 1.4;
}

.card__meta li svg {
  width: 14px;
  height: 14px;
  flex-shrink: 0;
  color: #aaa;
}

/* Skills */
.card__skills {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.skill-tag {
  font-size: 11px;
  font-weight: 500;
  color: #5865f2;
  background: #eef2ff;
  padding: 3px 9px;
  border-radius: 6px;
  letter-spacing: 0;
}

/* Achievements */
.card__achievements {
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding-top: 2px;
  border-top: 1px solid #f0f0f0;
}

.card__achievements li {
  font-size: 12px;
  color: #666;
  padding-left: 10px;
  position: relative;
  line-height: 1.6;
}

.card__achievements li::before {
  content: '·';
  position: absolute;
  left: 0;
  color: #bbb;
}

/* Link */
.card__link {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  font-size: 12.5px;
  font-weight: 600;
  color: #5865f2;
  margin-top: auto;
  padding-top: 4px;
  transition: gap 0.2s ease;
}

.card__link:hover {
  gap: 8px;
  color: #4752c4;
}

.card__link svg {
  width: 13px;
  height: 13px;
}
</style>

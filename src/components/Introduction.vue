<script setup>
const profile = {
  name: "김현영",
  career: "경력 9년 2개월",
  age: 35,
  address: "인천시 부평구",
  email: "gusdud2110@naver.com",
  phone: "010-2211-6177",
  license: [
    { date: "2015.03", name: "그래픽기술자격(GTQ) 1급" },
    { date: "2015.01", name: "컴퓨터활용능력" }
  ],
  skills: [
    "HTML", "CSS", "JavaScript", "Vue3", "React", "SCSS", "Tailwind", 
    "jQuery", "Bootstrap", "Git", "SVG", "Zeplin", "Figma", "Photoshop"
  ]
}

const infoItems = [
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>`,
    label: "이름", value: profile.name
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`,
    label: "나이", value: `${profile.age}세`
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>`,
    label: "주소", value: profile.address
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>`,
    label: "이메일", value: profile.email
  },
  {
    icon: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.54 3.44 2 2 0 0 1 3.53 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L7.91 9.91a16 16 0 0 0 6.18 6.18l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>`,
    label: "연락처", value: profile.phone
  },
]
</script>

<template>
  <section class="intro">

    <!-- Hero -->
    <div class="intro__hero">
      <div class="intro__hero-content">
        <p class="intro__label">ABOUT ME</p>
        <h1 class="intro__heading">
          <span class="intro__career">{{ profile.career }}</span>
          웹퍼블리셔<br />
          <em>{{ profile.name }}</em>입니다
        </h1>
        <p class="intro__sub">프로젝트 경험을 기반으로 한 실무 중심의 웹 개발 전문가입니다</p>
      </div>
      <div class="intro__hero-badge">
        <span>UI / UX</span>
        <span>Publishing</span>
        <span>Responsive</span>
      </div>
    </div>

    <!-- Main Content Grid -->
    <div class="intro__grid">

      <!-- Profile image -->
      <div class="intro__photo-wrap">
        <div class="intro__photo">
          <img src="/images/profile-image-new.jpg" alt="프로필 이미지" />
        </div>
        <div class="intro__photo-deco"></div>
      </div>

      <!-- Info -->
      <div class="intro__info">

        <!-- Profile -->
        <div class="intro__block">
          <h2 class="intro__block-title">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
            PROFILE
          </h2>
          <ul class="intro__profile-list">
            <li v-for="info in infoItems" :key="info.label">
              <span class="info-icon" v-html="info.icon"></span>
              <span class="info-label">{{ info.label }}</span>
              <span class="info-value">{{ info.value }}</span>
            </li>
          </ul>
        </div>

        <!-- License -->
        <div class="intro__block">
          <h2 class="intro__block-title">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="20" height="14" rx="2" ry="2"/><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"/></svg>
            LICENSE
          </h2>
          <ul class="intro__license-list">
            <li v-for="lic in profile.license" :key="lic.name">
              <span class="lic-date">{{ lic.date }}</span>
              <span class="lic-name">{{ lic.name }}</span>
            </li>
          </ul>
        </div>

        <!-- Skills -->
        <div class="intro__block">
          <h2 class="intro__block-title">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
            SKILLS
          </h2>
          <div class="intro__skills">
            <span v-for="skill in profile.skills" :key="skill" class="skill-chip">{{ skill }}</span>
          </div>
        </div>

      </div>
    </div>

  </section>
</template>

<style scoped>
/* ── Section Base ─────────────────────────── */
.intro {
  background: #0f1117;
  color: #e8e8e8;
  font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
}

/* ── Hero ─────────────────────────────────── */
.intro__hero {
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 48px 60px;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 24px;
  flex-wrap: wrap;
}

.intro__label {
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 3px;
  color: #5865f2;
  margin-bottom: 16px;
}

.intro__heading {
  font-size: clamp(28px, 4vw, 52px);
  font-weight: 800;
  line-height: 1.2;
  color: #fff;
  letter-spacing: -1.5px;
}

.intro__career {
  display: block;
  font-size: clamp(14px, 1.8vw, 20px);
  font-weight: 500;
  color: #5865f2;
  letter-spacing: 0;
  margin-bottom: 8px;
}

.intro__heading em {
  font-style: normal;
  color: #5865f2;
}

.intro__sub {
  margin-top: 20px;
  font-size: 14px;
  color: #6b7280;
  letter-spacing: -0.2px;
}

.intro__hero-badge {
  display: flex;
  flex-direction: column;
  gap: 8px;
  align-items: flex-end;
}

.intro__hero-badge span {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2px;
  color: #3a3f5c;
  text-transform: uppercase;
  border: 1px solid #1e2139;
  padding: 6px 14px;
  border-radius: 30px;
}

/* ── Main Grid ────────────────────────────── */
.intro__grid {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px 48px 100px;
  display: grid;
  grid-template-columns: 280px 1fr;
  gap: 48px;
  align-items: start;
}

/* ── Photo ────────────────────────────────── */
.intro__photo-wrap {
  position: relative;
  padding-top: 16px;
  padding-left: 16px;
}

.intro__photo-deco {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 2px solid #5865f2;
  border-radius: 20px;
  opacity: 0.35;
  z-index: 0;
}

.intro__photo {
  position: relative;
  z-index: 1;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.5);
}

.intro__photo img {
  width: 100%;
  display: block;
  border-radius: 16px;
  object-fit: cover;
}

/* ── Info ─────────────────────────────────── */
.intro__info {
  display: flex;
  flex-direction: column;
  gap: 36px;
}

.intro__block {
  background: #181c2a;
  border-radius: 16px;
  padding: 24px 28px;
  border: 1px solid #1e2238;
}

.intro__block-title {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 2.5px;
  color: #5865f2;
  margin-bottom: 18px;
  text-transform: uppercase;
}

.intro__block-title svg {
  width: 15px;
  height: 15px;
  flex-shrink: 0;
}

/* Profile List */
.intro__profile-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.intro__profile-list li {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
  color: #ccc;
}

.info-icon {
  display: flex;
  align-items: center;
  width: 16px;
  height: 16px;
  flex-shrink: 0;
  color: #5865f2;
}

.info-icon :deep(svg) {
  width: 15px;
  height: 15px;
}

.info-label {
  width: 52px;
  flex-shrink: 0;
  font-size: 11px;
  font-weight: 600;
  color: #555;
  letter-spacing: 0.5px;
  text-transform: uppercase;
}

.info-value {
  color: #e0e0e0;
  font-size: 13.5px;
}

/* License List */
.intro__license-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.intro__license-list li {
  display: flex;
  align-items: center;
  gap: 14px;
  font-size: 13.5px;
  color: #ccc;
}

.lic-date {
  font-size: 11px;
  font-weight: 600;
  color: #5865f2;
  background: rgba(88, 101, 242, 0.12);
  padding: 3px 9px;
  border-radius: 6px;
  white-space: nowrap;
  letter-spacing: 0.3px;
}

.lic-name {
  color: #ccc;
}

/* Skills */
.intro__skills {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.skill-chip {
  font-size: 12px;
  font-weight: 500;
  padding: 5px 12px;
  border-radius: 8px;
  background: #1e2238;
  color: #a0a8cc;
  border: 1px solid #282e48;
  transition: background 0.2s, color 0.2s;
  cursor: default;
}

.skill-chip:hover {
  background: #5865f2;
  color: #fff;
  border-color: #5865f2;
}

/* ── Responsive ───────────────────────────── */
@media (max-width: 900px) {
  .intro__grid {
    grid-template-columns: 1fr;
    padding: 20px 28px 80px;
  }

  .intro__photo-wrap {
    max-width: 260px;
    margin: 0 auto;
  }

  .intro__hero {
    padding: 80px 28px 40px;
    flex-direction: column;
    align-items: flex-start;
  }

  .intro__hero-badge {
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
  }
}

@media (max-width: 480px) {
  .intro__hero {
    padding: 60px 20px 32px;
  }

  .intro__grid {
    padding: 16px 20px 60px;
  }
}
</style>
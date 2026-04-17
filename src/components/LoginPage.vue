<template>
  <div class="login-wrapper">
    <!-- LEFT PANEL -->
    <div class="left-panel">
      <div class="brand">
        <img src="../assets/logo.png" alt="Team Achieve Logo" class="logo" />
      </div>

      <!-- Centered content -->
      <div class="left-center">
        <div class="hero-image-container">
          <img src="../assets/banner.png" alt="Team celebrating" class="hero-image" />
        </div>
        <div class="tagline">
          <p class="tagline-title">Team Achieve</p>
          <p class="tagline-sub">Your perfect solution for funding your desires</p>
        </div>
      </div>
    </div>

    <!-- RIGHT PANEL -->
    <div class="right-panel">
      <div class="form-card">
        <h1 class="form-title">Welcome Back</h1>
        <p class="form-subtitle">Enter your email address and password to access your account.</p>

        <LoginForm />
      </div>
    </div>
  </div>
</template>

<script setup>
import LoginForm from './LoginForm.vue'
</script>

<style scoped>
.login-wrapper {
  display: flex;
  min-height: 100vh;
}

/* LEFT PANEL */
.left-panel {
  width: 40%;
  background-color: var(--color-bg-left);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 2rem;
  position: relative;
}

.brand {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.4rem;
}

.left-center {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  gap: 1.5rem;
}

.logo {
  width: 198px;
  height: 97px;
  top: 24px;
  left: 45px;
}

.brand-name {
  font-size: 1rem;
  color: var(--color-text-muted);
  font-weight: 500;
}

.hero-image-container {
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
}

.hero-image {
  width: 100%;
  height: 260px;
  object-fit: cover;
  border-radius: 12px;
}

.tagline {
  text-align: center;
}

.tagline-title {
  color: var(--color-primary);
  font-weight: 700;
  font-size: 1.1rem;
}

.tagline-sub {
  font-size: 0.9rem;
  color: var(--color-text-muted);
  font-weight: 600;
}

/* RIGHT PANEL */
.right-panel {
  width: 60%;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 3rem 2rem;
}

.form-card {
  width: 100%;
  max-width: 480px;
}

.form-title {
  text-align: center;
  color: var(--color-primary);
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.form-subtitle {
  text-align: center;
  color: var(--color-text-muted);
  font-size: 0.9rem;
  margin-bottom: 2rem;
}

/* RESPONSIVE — Mobile */
@media (max-width: 768px) {
  .login-wrapper {
    flex-direction: column;
  }

  .left-panel {
    display: none; /* hide on mobile, matches the mobile mockup */
  }

  .right-panel {
    width: 100%;
    padding: 2rem 1.25rem;
  }
}
</style>

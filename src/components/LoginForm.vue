<template>
  <div class="login-form">
    <!-- Email -->
    <div class="field">
      <label for="email"> Email Address <span class="required">*</span> </label>
      <input
        id="email"
        v-model="email"
        type="email"
        placeholder="Enter your email"
        :class="{ 'input-error': errors.email }"
        @blur="validateEmail"
      />
      <span v-if="errors.email" class="error-msg">{{ errors.email }}</span>
    </div>

    <!-- Password -->
    <div class="field">
      <label for="password"> Password <span class="required">*</span> </label>
      <div class="password-wrapper" :class="{ 'input-error': errors.password }">
        <input
          id="password"
          v-model="password"
          :type="showPassword ? 'text' : 'password'"
          placeholder="Enter your password"
          @blur="validatePassword"
        />
        <button type="button" class="toggle-eye" @click="showPassword = !showPassword">
          <EyeOff v-if="showPassword" :size="18" />
          <Eye v-else :size="18" />
        </button>
      </div>
      <span v-if="errors.password" class="error-msg">{{ errors.password }}</span>
    </div>

    <div class="form-extras">
      <label class="remember">
        <input type="checkbox" v-model="rememberMe" />
        Remember me
      </label>
      <a href="#" class="forgot-link">Forgot Password?</a>
    </div>

    <button class="btn-signin" @click="handleSubmit" :disabled="isLoading">
      <span v-if="isLoading">Signing in...</span>
      <span v-else>Sign in</span>
    </button>

    <p class="signup-text">Don't have an account? <a href="#" class="signup-link">Sign up</a></p>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { Eye, EyeOff } from 'lucide-vue-next'

const email = ref('')
const password = ref('')
const rememberMe = ref(false)
const showPassword = ref(false)
const isLoading = ref(false)

const errors = reactive({
  email: '',
  password: '',
})

function validateEmail() {
  if (!email.value) {
    errors.email = 'Email is required.'
  } else if (!/^\S+@\S+\.\S+$/.test(email.value)) {
    errors.email = 'Please enter a valid email address.'
  } else {
    errors.email = ''
  }
}

function validatePassword() {
  if (!password.value) {
    errors.password = 'Password is required.'
  } else if (password.value.length < 6) {
    errors.password = 'Password must be at least 6 characters.'
  } else {
    errors.password = ''
  }
}

function handleSubmit() {
  validateEmail()
  validatePassword()

  if (errors.email || errors.password) return

  isLoading.value = true

  // Simulate API call
  setTimeout(() => {
    isLoading.value = false
    alert(`Logged in as ${email.value}`)
  }, 1500)
}
</script>

<style scoped>
.login-form {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.field {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

label {
  font-size: 0.9rem;
  font-weight: 600;
  color: #333;
}

.required {
  color: var(--color-error);
}

input[type='email'],
input[type='text'],
input[type='password'] {
  width: 100%;
  padding: 0.7rem 1rem;
  border: 1px solid var(--color-border);
  border-radius: 6px;
  font-size: 0.95rem;
  outline: none;
  transition: border-color 0.2s;
}

input:focus {
  border-color: var(--color-primary);
}

input.input-error {
  border-color: var(--color-error);
}

.error-msg {
  font-size: 0.78rem;
  color: var(--color-error);
}

.password-wrapper {
  display: flex;
  align-items: stretch;
  border: 1px solid var(--color-border);
  border-radius: 6px;
  overflow: hidden;
  transition: border-color 0.2s;
}

.password-wrapper:focus-within {
  border-color: var(--color-primary);
}

.password-wrapper.input-error {
  border-color: var(--color-error);
}

.password-wrapper input {
  flex: 1;
  padding: 0.7rem 1rem;
  border: none;
  outline: none;
  font-size: 0.95rem;
  background: transparent;
}

.toggle-eye {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 0.85rem;
  background-color: #f7f7f7;
  border: none;
  border-left: 1px solid var(--color-border);
  cursor: pointer;
  color: #888;
  transition: background-color 0.2s;
}

.toggle-eye:hover {
  background-color: #e8e8e8;
}

.form-extras {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.85rem;
}

.remember {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  cursor: pointer;
}

.forgot-link {
  color: var(--color-primary);
  text-decoration: none;
  font-weight: 500;
}

.forgot-link:hover {
  text-decoration: underline;
}

/* Sign In Button */
.btn-signin {
  width: 100%;
  padding: 0.85rem;
  background-color: var(--color-primary);
  color: white;
  font-size: 1rem;
  font-weight: 700;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.btn-signin:hover:not(:disabled) {
  background-color: var(--color-primary-hover);
}

.btn-signin:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

/* Sign Up */
.signup-text {
  text-align: center;
  font-size: 0.875rem;
  color: var(--color-text-muted);
}

.signup-link {
  color: var(--color-primary);
  font-weight: 600;
  text-decoration: none;
}

.signup-link:hover {
  text-decoration: underline;
}
</style>

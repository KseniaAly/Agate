<script setup lang="ts">
import { ref, computed } from 'vue';

const name = ref('');
const phone = ref('');
const email = ref('');
const consent = ref(false);
const errors = ref({
  name: '',
  phone: '',
  email: '',
  consent: ''
});
const isSubmitted = ref(false);

const validateName = () => {
  if (!name.value.trim()) {
    errors.value.name = 'Обязательное поле';
  } else if (!/^[а-яА-ЯёЁa-zA-Z\s-]{2,25}$/.test(name.value)) {
    errors.value.name = 'Только буквы и дефисы (2-25 символов)';
  } else {
    errors.value.name = '';
  }
};

const validatePhone = () => {
  if (!phone.value.trim()) {
    errors.value.phone = 'Обязательное поле';
  } else if (!/^(\+7|8)[\d\s-]{10,15}$/.test(phone.value)) {
    errors.value.phone = 'Формат: +7 XXX XXX XX XX';
  } else {
    errors.value.phone = '';
  }
};

const validateEmail = () => {
  if (!email.value.trim()) {
    errors.value.email = 'Обязательное поле';
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email.value)) {
    errors.value.email = 'Некорректный email';
  } else {
    errors.value.email = '';
  }
};

const validateConsent = () => {
  errors.value.consent = consent.value ? '' : 'Необходимо согласие';
};

const isValid = computed(() => {
  return !errors.value.name &&
      !errors.value.phone &&
      !errors.value.email &&
      consent.value;
});

const submitForm = () => {
  validateName();
  validatePhone();
  validateEmail();
  validateConsent();

  if (isValid.value) {
    console.log('Форма отправлена', {
      name: name.value,
      phone: phone.value,
      email: email.value,
      consent: consent.value
    });
    isSubmitted.value = true;
    resetForm(); // Очищаем форму
    setTimeout(() => isSubmitted.value = false, 3000); // Скрываем сообщение через 5 секунд
  }
};

const resetForm = () => {
  name.value = '';
  phone.value = '';
  email.value = '';
  consent.value = false;
};
</script>

<template>
  <div class="container">
    <div class="feedback-form">
      <h2 class="title">Остались вопросы? С удовольствием ответим на них</h2>
      <p class="subtitle">Заполните форму обратной связи и наш сотрудник свяжется с вами в ближайшее время.</p>
      <div v-if="isSubmitted" class="success-message">
        Форма успешно отправлена! Мы свяжемся с вами в ближайшее время.
      </div>

      <form v-if="!isSubmitted" @submit.prevent="submitForm" class="form-three">
        <div class="form-group">
          <input
              v-model="name"
              @blur="validateName"
              type="text"
              class="input-field"
              :class="{ 'error': errors.name }"
              placeholder="Имя"
          >
          <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
        </div>

        <div class="form-group">
          <input
              v-model="phone"
              @blur="validatePhone"
              type="tel"
              class="input-field"
              :class="{ 'error': errors.phone }"
              placeholder="Телефон"
          >
          <span v-if="errors.phone" class="error-message">{{ errors.phone }}</span>
        </div>

        <div class="form-group">
          <input
              v-model="email"
              @blur="validateEmail"
              type="email"
              class="input-field"
              :class="{ 'error': errors.email }"
              placeholder="E-mail"
          >
          <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
        </div>

        <div class="consent-group" :class="{ 'error': errors.consent }">
          <input
              type="checkbox"
              id="consent"
              v-model="consent"
              @change="validateConsent"
              class="consent-checkbox"
          >
          <label for="consent" class="consent-label">Даю согласие на обработку персональных данных</label>
          <span v-if="errors.consent" class="error-message">{{ errors.consent }}</span>
        </div>

        <button type="submit" class="submit-button">Отправить</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Onest:wght@400;500;600&display=swap');
* {
  font-size: 18px;
  font-family: 'Onest';
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  width: 100%;
  display: flex;
  justify-content: center;
  margin: 0 auto;
  padding: 20px;
  overflow-x: hidden;
  background-color: #1C1919;
}

.feedback-form {
  padding: 50px;
  width: 100%;
}

.title {
  font-size: 30px;
  color: #fff;
  margin-bottom: 15px;
  text-align: center;
  font-weight: normal;
}

.form-three {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.subtitle {
  color: #fff;
  margin-bottom: 20px;
  font-size: 14px;
  text-align: center;
}

.form-group {
  margin-bottom: 26px;
  display: flex;
  flex-direction: column;
}

.input-field {
  width: 400px;
  height: 42px;
  padding: 12px 15px;
  border: 3px solid #880003;
  border-radius: 5px;
  font-size: 16px;
  transition: border-color 0.3s;

}

.input-field.error {
  border-color: #ff3333;
}

.error-message {
  color: #ff3333;
  font-size: 12px;
  margin-top: 5px;
}

.input-field:focus {
  border-color: #880003;
  outline: none;
  color: #1C1919;
}

.consent-group {
  display: flex;
  align-items: center;
  margin-bottom: 26px;
  position: relative;
  width: 100%;
  max-width: 400px;
}

.consent-group.error {
  padding-bottom: 20px;
}

.consent-checkbox {
  margin-right: 10px;
  width: 18px;
  height: 18px;

}

.consent-label {
  color: #ffffff;
  font-size: 14px;
  text-decoration: underline;
}

.submit-button {
  width: 147px;
  height: 42px;
  background-color: #880003;
  color: #FFFFFF;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 14px;
  font-weight: normal;
  transition: background-color 0.3s;
}

.submit-button:hover {
  background-color: #ffffff;
  color: #880003;
}

.success-message {
  color: #880003;
  background-color: #ffffff;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 20px;
  text-align: center;
  border: 3px solid #880003;
  animation: fadeIn 0.5s;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@media (max-width: 768px) {
  .feedback-form {
    padding: 30px;
  }

  .title {
    font-size: 26px;
  }

  .input-field {
    height: 40px;
  }
}

@media (max-width: 480px) {
  .feedback-form {
    padding: 20px;
  }

  .title {
    font-size: 22px;
  }

  .subtitle {
    font-size: 13px;
  }

  .submit-button {
    width: 100%;
    max-width: 400px;
  }
}
</style>
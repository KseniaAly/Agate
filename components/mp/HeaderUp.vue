<script setup lang="ts">
import { ref } from 'vue';

const activeNavItem = ref('');
const searchQuery = ref('');
const isMobileMenuOpen = ref(false);

const navItems = [
  { name: 'Каталог продукции', link: '/catalog' },
  { name: 'Бренды', link: '' },
  { name: 'Сервис и запасные части', link: 'https://agat-technic.ru/nn/news/' },
  { name: 'Акции', link: 'https://agat-technic.ru/nn/specials/' },
  { name: 'Услуги', link: 'https://agat-technic.ru/nn/articles/' },
  { name: 'О компании', link: 'https://agat-technic.ru/nn/about/' },
  { name: 'Контакты', link: 'https://agat-technic.ru/nn/contacts/' }
];

const setActiveItem = (item: string) => {
  activeNavItem.value = item;
  isMobileMenuOpen.value = false;
};

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
</script>

<template>
  <header class="header">
    <div class="top-header">
      <div class="header-content">
        <div class="logo">
          <img src="/img/logo.png">
        </div>
        <div class="contact-info">
          <div class="phone">
            <div class="phone-number">7 (831) 2-000-000</div>
            <a href="#" class="callback">Заказать звонок</a>
          </div>
          <div class="location">
            <img src="/img/icon.png">
            <span>Нижний Новгород</span>
          </div>
        </div>
        <div class="search">
          <input
              v-model="searchQuery"
              type="text"
              placeholder="Поиск по сайту"
              class="search-input"
          >
          <svg class="search-icon" width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M7.33333 12.6667C10.2789 12.6667 12.6667 10.2789 12.6667 7.33333C12.6667 4.38781 10.2789 2 7.33333 2C4.38781 2 2 4.38781 2 7.33333C2 10.2789 4.38781 12.6667 7.33333 12.6667Z" stroke="#880003" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M14 14L11.1 11.1" stroke="#880003" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <button class="mobile-menu-toggle" @click="toggleMobileMenu">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
      <nav class="navigation" :class="{ 'mobile-open': isMobileMenuOpen }">
        <ul class="nav-list">
          <li
              v-for="item in navItems"
              :key="item.name"
              :class="{ 'active': activeNavItem === item.name }"
              @click="setActiveItem(item.name)"
          >
            <a :href="item.link" class="nad">{{ item.name }}</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Onest:wght@400;500;600&display=swap');

* {
  font-family: 'Onest', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.header {
  background-color: #1C1919;
  color: white;
  width: 100%;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1330px;
  margin: 0 auto;
  padding: 15px 20px;
  gap: 20px;
}

.logo {
  display: flex;
  flex-direction: column;
  min-width: 120px;
}

.contact-info {
  display: flex;
  align-items: center;
  gap: 30px;
}

.phone {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.phone-number {
  font-size: 18px;
  font-weight: 500;
}

.callback {
  font-size: 14px;
  color: white;
  text-decoration: underline;
  margin-top: 5px;
  transition: color 0.3s;
  font-weight: normal;
}

.callback:hover {
  color: #880003;
}

.location {
  display: flex;
  align-items: end;
  justify-content: end;
  gap: 8px;
  font-size: 14px;
  text-decoration: underline;
  font-weight: normal;
}

.search {
  position: relative;
  width: 300px;
}

.search-input {
  width: 100%;
  padding: 8px 30px 8px 15px;
  border: 2px solid #880003;
  border-radius: 5px;
  background-color: white;
  color: #1C1919;
  font-size: 14px;
}

.search-input:focus {
  outline: none;
  border-color: #880003;
}

.search-icon {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  pointer-events: none;
}

.nav-list {
  display: flex;
  justify-content: space-between;
  list-style: none;
  gap: 20px;
  max-width: 1330px;
  margin: 0 auto;
  border-top: solid 1px #fff;
  padding: 10px 20px;
}

.nav-list li {
  padding: 10px 15px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.3s;
  border-radius: 5px;
}

.nav-list li:hover,
.nav-list li.active {
  background-color: #880003;
}

.mobile-menu-toggle {
  display: none;
  background: none;
  border: none;
  width: 30px;
  height: 24px;
  position: relative;
  cursor: pointer;
  padding: 0;
}

.mobile-menu-toggle span {
  display: block;
  position: absolute;
  height: 3px;
  width: 100%;
  background: white;
  border-radius: 3px;
  opacity: 1;
  left: 0;
  transform: rotate(0deg);
  transition: .25s ease-in-out;
}

.nad{
  color: #FFFFFF;
  text-decoration: none;
}

.mobile-menu-toggle span:nth-child(1) {
  top: 0px;
}

.mobile-menu-toggle span:nth-child(2),
.mobile-menu-toggle span:nth-child(3) {
  top: 10px;
}

.mobile-menu-toggle span:nth-child(4) {
  top: 20px;
}

@media (max-width: 1080px) {
  .mobile-menu-toggle {
    display: block;
  }

  .navigation {
    display: none;
    border-top: none;
  }

  .navigation.mobile-open {
    display: block;
    padding: 0;
  }

  .nav-list {
    flex-direction: column;
    gap: 0;
    padding: 0;
  }

  .nav-list li {
    padding: 15px 20px;
    border-bottom: 1px solid #333;
    text-align: center;
  }

  .nav-list li:hover,
  .nav-list li.active {
    background-color: #880003;
  }

  .phone-number {
    font-size: 12px;
    font-weight: 500;
  }
}

@media (max-width: 900px) {
  .contact-info {
    gap: 15px;
  }

  .search {
    width: 180px;
  }

  .phone-number {
    font-size: 12px;
    font-weight: 500;
  }

  .contact-info{
    gap: 5px;
  }
}

@media (max-width: 770px) {
  .header-content {
    padding: 15px;
  }

  .contact-info {
    display: none;
  }

  .search {
    width: 200px;
    margin-right: 15px;
  }
}

@media (max-width: 600px) {
  .search {
    width: 150px;
  }
}

@media (max-width: 480px) {
  .header-content {
    padding: 10px 15px;
  }

  .logo {
    width: 120px;
  }

  .search {
    width: 120px;
    margin-right: 10px;
  }
}
</style>
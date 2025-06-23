<script setup lang="ts">
const socialLinks = {
  telegram: 'https://telegram.me/AGAT_bot',
  whatsapp: 'https://api.whatsapp.com/send?phone=79873901000',
  viber: '',
  vk: 'https://vk.com/agattdb',
  youtube: 'https://www.youtube.com/channel/UC8GYnOpDvozXPVaxupKWxAw?si=9w57O_FNZij0cLvA',
  yandex: 'https://sso.passport.yandex.ru/push?uuid=cca10011-0297-4a0a-89e9-7ba19b722f8f&retpath=https%3A%2F%2Fdzen.ru%2Fapi%2Fredirect%2Fvk-sso-for-log%3ForiginalUrl%3Dhttps%253A%252F%252Fdzen.ru%252Fagattdb%253Fshare_to%253Dlink%26utm_referrer%3Dagat-technic.ru'
};
</script>

<template>
  <footer class="footer">
    <div class="footer-background">
      <div class="background-overlay"></div>
    </div>
    <div class="footer-top">
      <div class="footer-top-content">
        <div class="messengers">
          <h3>Мы в мессенджерах:</h3>
          <a :href="socialLinks.telegram" target="_blank" class="messenger-item">
            <img src="/img/telegram.png" alt="Telegram" class="icon">
            <span>Telegram</span>
          </a>
          <a :href="socialLinks.whatsapp" target="_blank" class="messenger-item">
            <img src="/img/whatsapp.png" alt="WhatsApp" class="icon">
            <span>WhatsApp</span>
          </a>
          <a :href="socialLinks.viber" target="_blank" class="messenger-item">
            <img src="/img/viber.png" alt="Viber" class="icon">
            <span>Viber</span>
          </a>
        </div>
        <div class="logo-contacts">
          <img src="/img/Group.png">
          <div class="contact-info">
            <div class="phone">+7 (831) 2-000-000</div>
            <div class="address">Нижний Новгород, ул. Ларина, 23</div>
          </div>
        </div>
        <div class="socials">
          <h3>Мы в социальных сетях:</h3>
          <a :href="socialLinks.vk" target="_blank" class="social-item">
            <img src="/img/vk.png" alt="VK" class="icon">
            <span>Вконтакте</span>
          </a>
          <a :href="socialLinks.youtube" target="_blank" class="social-item">
            <img src="/img/youtube.png" alt="YouTube" class="icon">
            <span>YouTube</span>
          </a>
          <a :href="socialLinks.yandex" target="_blank" class="social-item">
            <img src="/img/yndex.png" alt="Yandex Zen" class="icon">
            <span>Яндекс.Дзен</span>
          </a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <div class="footer-text">
        Вся представленная на сайте информация, касающаяся автомобилей и сервисного обслуживания, носит информационный характер и не является публичной офертой, определяемой положениями ст. 437 (2) ГК РФ. Все цены и спецпредложения, указанные на данном сайте носят исключительно информационный характер и являются максимально рекомендуемыми розничными ценами и спецпредложениями по расчетам дистрибьюторов и могут отличаться от цен других дилеров. Для получения подробной информации просьба обращаться в ДЦ компании АГАТ. Опубликованная на данном сайте информация может быть изменена в любое время без предварительного уведомления.
      </div>

      <div class="footer-links">
        <div class="links-block">
          <div>© ООО «ТД «Агат» 2008—2022</div>
          <div>Все права защищены</div>
        </div>

        <div class="links-block">
          <div>Обратная связь</div>
          <a href="mailto:feedback@agatgroup.com" class="footer-link">feedback@agatgroup.com</a>
        </div>

        <div class="links-block">
          <a href="https://agat-technic.ru/nn/agreement/" class="footer-link">Защита персональных данных</a>
          <a href="https://agat-technic.ru/upload/files/agreement/bdefc89ef2c6ea697cc5f0d6e280f064.pdf" class="footer-link">Юридическая информация</a>
        </div>
      </div>
    </div>
  </footer>
</template>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Onest:wght@400;500;600&display=swap');

* {
  font-family: 'Onest', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.footer {
  position: relative;
  background-color: #1C1919;
  color: white;
  width: 100%;
  overflow: hidden;
}

.footer-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('/img/Mask group.png');
  background-size: cover;
  background-position: center;
  z-index: 0;
}

.background-overlay {
  width: 100%;
  height: 100%;
  background-color: rgba(28, 25, 25, 0.82);
  backdrop-filter: blur(40px);
}

.footer-top {
  position: relative;
  padding: 50px 0;
  z-index: 1;
}

.footer-top-content {
  display: flex;
  justify-content: space-around;
  align-items: center;
  max-width: 1330px;
  margin: 0 auto;
}

.messengers, .socials {
  display: flex;
  flex-direction: column;
  gap: 22px;
}

.messenger-item, .social-item {
  display: flex;
  align-items: center;
  gap: 10px;
}

.icon {
  width: 24px;
  height: 24px;
  filter: brightness(0) invert(1);
}

.logo-contacts {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.phone {
  font-size: 18px;
  font-weight: 500;
}

.address {
  font-size: 14px;
  opacity: 0.8;
}

h3 {
  font-size: 18px;
  font-weight: 500;
  margin-bottom: 10px;
}

.footer-bottom {
  position: relative;
  padding: 30px 0;
  z-index: 1;
  max-width: 1330px;
  margin: 0 auto;
  border-top: solid 1px #fff;
}

.footer-text {
  font-size: 12px;
  line-height: 1.5;
  margin-bottom: 30px;
  opacity: 0.8;
}

.footer-links {
  display: flex;
  justify-content: start;
  flex-wrap: wrap;
  gap: 20px;
  font-weight: normal;
}

.links-block {
  display: flex;
  flex-direction: column;
  gap: 5px;
  font-size: 12px;
}

.messenger-item,
.social-item,
.footer-link {
  color: white;
  text-decoration: none;
  transition: color 0.3s ease;
}

.messenger-item:hover,
.social-item:hover,
.footer-link:hover {
  text-decoration: underline;
}

.messenger-item,
.social-item {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
}

.footer-link {
  text-decoration: underline;
}

.footer-link:hover {
  text-decoration: underline;
  color: #dd424a;
}

@media (max-width: 768px) {
  .footer-top-content {
    flex-direction: column;
    gap: 30px;
    align-items: center;
  }

  .messengers, .socials {
    align-items: center;
    text-align: center;
  }

  .logo-contacts {
    order: -1;
    margin-bottom: 30px;
  }

  .footer-links {
    flex-direction: column;
    gap: 15px;
  }
}
</style>

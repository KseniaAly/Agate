<script setup lang="ts">

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
          <div class="messenger-item">
            <img src="/img/telegram.png" alt="Telegram" class="icon">
            <span>Telegram</span>
          </div>
          <div class="messenger-item">
            <img src="/img/whatsapp.png" alt="WhatsApp" class="icon">
            <span>WhatsApp</span>
          </div>
          <div class="messenger-item">
            <img src="/img/viber.png" alt="Viber" class="icon">
            <span>Viber</span>
          </div>
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
          <div class="social-item">
            <img src="/img/vk.png" alt="VK" class="icon">
            <span>Вконтакте</span>
          </div>
          <div class="social-item">
            <img src="/img/youtube.png" alt="YouTube" class="icon">
            <span>YouTube</span>
          </div>
          <div class="social-item">
            <img src="/img/yndex.png" alt="Yandex Zen" class="icon">
            <span>Яндекс.Дзен</span>
          </div>
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
          <div>feedback@agatgroup.com</div>
        </div>

        <div class="links-block">
          <div>Защита персональных данных</div>
          <div>Юридическая информация</div>
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
  text-decoration: underline;
}

.links-block {
  display: flex;
  flex-direction: column;
  gap: 5px;
  font-size: 12px;
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

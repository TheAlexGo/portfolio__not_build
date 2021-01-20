<template>
  <div class="container-fluid p-0">
    <header class="fixed-top w-100">
      <b-container>
        <b-row class="d-flex align-items-center">
          <b-navbar toggleable="lg" class="w-100">
            <b-container class="p-0">
              <b-row class="w-100">
                <b-col lg="4" cols="12">
                  <b-navbar-brand href="#">
                    <span class="logo">
                      Александр<span class="text-primary">.</span>
                    </span>
                  </b-navbar-brand>
                  <b-navbar-toggle target="nav-collapse" class="float-right"></b-navbar-toggle>
                </b-col>
                <b-col lg="8" cols="12" class="links">
                  <b-collapse id="nav-collapse" is-nav class="justify-content-between">
                    <b-navbar-nav v-for="link in links"
                                  :key="link.text"
                                  class="nav-link p-0">
                      <b-nav-item :href="link.href">{{ link.text }}</b-nav-item>
                    </b-navbar-nav>
                  </b-collapse>
                </b-col>
              </b-row>
            </b-container>
          </b-navbar>
        </b-row>
      </b-container>
    </header>
    <main>
      <section id="hello">
        <b-container>
          <b-row>
            <b-col xl="6" lg="6" md="12" sm="12" order-xl="1" order-lg="1" order="2" class="block_left">
              <div class="name">
                <h1>
                  Я - Александр Гордеев<span class="text-primary">.</span>
                </h1>
              </div>
              <div class="desc">
                <p class="text-secondary">
                  Здравствуйте! Я занимаюсь Front-end разработкой с 2018 года. На данный момент, я работаю в компании
                  Site-Master, должность - специалист тех-отдела. Занимаюсь разработкой, поддержкой и оптимизацией
                  различных сайтов. На моём счету 10-ки разнообразных проектов для разных компаний: начиная от обычных
                  лэндингов, заканчивая интернет-магаинами. За полгода работы в SM я изучил множество различных CMS:
                  Bitrix, Opencart, Wordpress, cs-cart и др.
                  В ближайшем будущем хочу полностью перейти на фронт (React или Angular), а потом и на full-stack.
                  Я общительный, коммуникабельный, спокойный и ответственный специалист.
                </p>
              </div>
              <div>
                <div v-for="data in datas" :key="datas.text" class="d-flex data-item mt-2 mb-2">
                  <div class="w-25 first_text">{{ data.text }}</div>
                  <a :href="data.href" class="w-75 text-secondary second_text">{{ data.desc }}</a>
                </div>
                <div class="d-flex data-item mt-2 mb-2">
                  <div class="w-25 first_text">Social</div>
                  <div class="w-25 d-flex justify-content-between">
                    <a style="font-size: 14px;" v-for="soc in social" :key="soc.id" :href="soc.web.href" target="_blank">
                      <i :class="soc.web.class"></i>
                    </a>
                  </div>
                </div>
                <div class="d-flex justify-content-between mt-4">
                  <b-button variant="primary" class="me_button">Напишите мне</b-button>
                  <b-button variant="outline-secondary" class="me_button"><a href="../static/resume.pdf" target="_blank">Скачать</a></b-button>
                </div>
              </div>
            </b-col>
            <b-col xl="6" lg="6" md="12" sm="12" order-xl="2" order-lg="2" order="1" class="block_right">
              <img
                style="width: 100%; height: 100%; max-height: 345px; object-fit: cover;"
                src="../assets/avatar.jpg"
                alt="Гордеев Александр" />
            </b-col>
          </b-row>
        </b-container>
      </section>
      <section v-for="theme in themes" :id="theme.text_id" :key="theme.id">
        <b-container v-if="theme.text_id !== 'portfolio'" >
          <b-row>
            <b-col md="4" cols="12" class="block_content">
              <h2>{{ theme.name }}<span class="text-primary">.</span></h2>
              <p class="text-secondary">
                {{ theme.desc }}
              </p>
              <div class="zigzag d-none d-md-block">
                <svg stroke="#efefef" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" viewBox="0 0 105 20" xml:space="preserve">
                    <g fill="none">
                            <polyline class="st1" points="2.5,5 16.8,15 31.1,5 45.3,15 59.6,5 73.9,15 88.2,5 102.5,15   "></polyline>
                        </g>
          </svg>
                <svg stroke="#007bff" xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" viewBox="0 0 105 20" xml:space="preserve">
                    <g>

                        <g>
                            <polyline class="st1" points="2.5,5 16.8,15 31.1,5 45.3,15 59.6,5 73.9,15 88.2,5 102.5,15   "></polyline>
                        </g>
                    </g>
                </svg>
              </div>
            </b-col>
            <b-col md="8" cols="12" class="d-flex flex-wrap p-0">
              <b-container>
                <b-row>
                  <b-col lg="6" cols="12" v-if="theme.text_id === 'skills'"
                         v-for="skill in theme.data"
                         :key="skill.id"
                         class="pr-3 pl-3">
                    <h5>{{ skill.name }}</h5>
                    <p class="text-secondary desc_text">{{ skill.desc }}</p>
                    <hr v-if="skill.id <= theme.data.length-2">
                  </b-col>
                  <b-col cols="12" v-if="theme.text_id === 'edu'"
                       v-for="edu in theme.data"
                       :key="edu.id"
                       class="pr-3 pl-3">
                    <div class="d-flex">
                      <b-container>
                        <b-row class="align-items-baseline">
                          <h5 style="max-width: 70%;">{{ edu.name }}</h5>
                          <b-col md="3" cols="12" class="w-25 p-0 ml-md-3 text-secondary">{{ edu.city }}</b-col>
                        </b-row>
                      </b-container>
                    </div>
                    <span>{{ edu.time }}</span>
                    <p class="text-secondary"><i>{{ edu.desc }}</i></p>
                    <hr v-if="edu.id <= theme.data.length-1">
                  </b-col>
                  <b-col cols="12" v-if="theme.text_id === 'contact'" >
                    <form action="http://localhost:63343/portfolio/assets/script.php" method="POST" class="contact_form">
                      <b-container class="p-0">
                        <b-row>
                          <b-col cols="12" md="4">
                            <div class="contact_form__name">
                              <label class="w-100 mt-3">
                                <input class="w-100" type="text" name="name" placeholder="Имя">
                              </label>
                              <label class="w-100 mt-3">
                                <input class="w-100" type="text" name="email" placeholder="Email">
                              </label>
                            </div>
                          </b-col>
                          <b-col cols="12" md="8 mt-3">
                            <label class="w-100 h-100">
                              <textarea class="w-100 h-100" rows="5" cols="45" name="message" placeholder="Введите Ваше сообщение..."></textarea>
                            </label>
                          </b-col>
                          <b-col cols="12">
                            <b-button variant="primary" class="float-right me_button mt-3" type="submit" value="Отправить">Отправить</b-button>
                          </b-col>
                        </b-row>
                      </b-container>
                    </form>
                  </b-col>
                </b-row>
              </b-container>
            </b-col>
          </b-row>
        </b-container>
        <b-container v-if="theme.text_id === 'portfolio'" >
          <b-row>
            <b-col cols="12">
              <h2>{{ theme.name }}<span class="text-primary">.</span></h2>
            </b-col>
            <b-col cols="12">
              <b-tabs>
                <b-tab v-for="item in theme.portfolios" :key="item.id" :title="item.name">
                  <b-container class="p-0">
                    <b-row class="justify-content-sm-between justify-content-center flex-row flex-wrap">
                      <Item
                        v-for="img in activeWeb_sites(web_sites, item.name)"
                        :key="img.id"
                        :product-data="img" />
                    </b-row>
                  </b-container>
                </b-tab>
              </b-tabs>
            </b-col>
          </b-row>
        </b-container>
      </section>
    </main>
    <footer>
      <b-container>
        <b-row>
          <b-col cols="12" class="d-flex justify-content-center align-items-center">
            <p class="m-0">
              Copyright {{ years_now() }} Александр Гордеев.
            </p>
          </b-col>
        </b-row>
      </b-container>
    </footer>
  </div>
</template>

<script>
import Item from "../components/item_portfolio"
export default {
  components: {
    Item
  },
  data() {
    return {
      active: true,
      isPopShow: false,
      links: [
        { text: "Вступление", href: '#hello' },
        { text: "Способности", href: '#skills' },
        { text: "Обучение", href: '#edu' },
        { text: "Портфолио", href: '#portfolio' },
        // { text: "feedback", href: '#feedback' },
        { text: "Свяжитесь со мной", href: '#contact' },
      ],
      datas: [
        { text: "Телефон", desc: "8 (951) 674-24-89", href: "tel:89516742489" },
        { text: "Email", desc: "alex280702@mail.ru", href: "mailto:89516742489" },
      ],
      social: [
        { web: { class: "fa fa-vk", href: "https://vk.com/gordeev0207"} },
        { web: { class: "fa fa-facebook", href: "https://www.facebook.com/profile.php?id=100009139240580"} },
        { web: { class: "fa fa-twitter", href: "https://twitter.com/StanFordPines17"} },
        { web: { class: "fa fa-instagram", href: "https://www.instagram.com/thealexg0/"} },
        { web: { class: "fa fa-github", href: "https://github.com/TheAlexGo"} }
      ],
      themes: [
        { text_id: 'skills',
          name: 'Способности',
          desc: 'Меня вдохновляет работа со сложными и интересными проекты с такими же заинтересованными, как и я, специалистами',
          data: [
            { id: 1, name: 'Frontend Development', desc: 'Javascript, jQuery, Vue.JS, Nuxt.JS.' },
            { id: 2, name: 'Backend Development', desc: 'PHP, Python, MySQL.' },
            { id: 3, name: 'CMS', desc: 'WordPress, Bitrix, Opencart, MODX, Joomla.' },
            { id: 4, name: 'Software', desc: 'WebStorm, PHPStrom, PyCharm, FileZilla, SublimeText.' },
          ] },
        { text_id: 'edu',
          name: 'Образование',
          desc: 'Всю свою жизнь я был уверен в важности образования, поэтому каждый день я стараюсь изучать что-то новое',
          data: [
            { id: 1,
              name: 'МОУ "Киришский лицей"',
              city: 'Кириши',
              time: 'Сентябрь 2009 – Июнь 2018',
              desc: 'Окончил со средним баллом аттестата 4.56' },
            { id: 2,
              name: 'Колледж телекоммуникаций при СПбГУТ им. Бонч-Бруевича (СПбКТ, бывш. ЛЭТС им. Кренкеля)',
              city: 'Санкт-Петербург',
              time: 'Сентябрь 2018 - ???',
              desc: '3 курс, на данный момент средния балл аттестата: 5.0' },
          ] },
        {
          text_id: 'portfolio',
          name: 'Портфолио',
          portfolios: [
            { name: 'Все проекты' },
            { name: 'Сайты' },
            { name: 'UI/UX дизайн' }
          ],
        },
        {
          text_id: 'contact',
          name: 'Свяжитесь со мной',
          desc: 'Вы работаете над чем-то большим и трудным? Нуждаетесь в молодом специалисте?' +
            ' Напишите мне и начнём наше сотрудничество! '
        }
        ],
      web_sites: [
        { section: 'Сайты',
          name: 'Osk-Valday',
          time: 'Март, 2020',
          href: 'http://www.osk-valday.ru',
          desc: 'Данный сайт был специально разработан для строительной организации ООО "ОСК Валдай".',
          type: 'CMS',
          type_engine: 'Wordpress',
          version_engine: '5.4.2',
          modules: ['Autoptimize (для оптимизации CSS, JS, изображений и др.)',
            'Contact Form 7 (для осуществления отправки запросов клиента с сайта на почту организации)'],
          technology: ['HTML5', 'CSS3', 'Bootstrap 4', 'JavaScript', 'jQuery', 'PHP', 'SVG'],
          photo: require('../assets/portfolio/osk-valday.png')
        },
        { section: 'UI/UX дизайн',
          name: 'Самогонщик Сэм',
          href: '',
          time: 'Апрель, 2020',
          desc: 'Шаблон сайта самогонных аппаратов.',
          type: 'self-written',
          technology: ['HTML5', 'CSS3'],
          photo: require('../assets/portfolio/SEMSAM.png')
        },
        { section: 'UI/UX дизайн',
          name: 'dezik.com.ua',
          href: 'https://dezik.com.ua',
          time: 'Январь, 2020',
          desc: 'Обновление дизайна украинского интернет-магазина инструментов стерилизации и дезинфекции.',
          type: 'CMS',
          type_engine: 'CS Cart',
          version_engine: '3.1.2.6',
          technology: ['HTML5', 'CSS3', 'JavaScript', 'PHP'],
          photo: require('../assets/portfolio/dezik.com.ua.png')
        },
        { section: 'UI/UX дизайн',
          name: 'Золотой дракон',
          href: '',
          time: 'Июнь, 2019',
          desc: 'Обновление дизайна сайта-ресторана восточной кухни в Вологде.',
          type: 'CMS',
          type_engine: 'Opencart',
          version_engine: '2.0.3.1',
          technology: ['HTML5', 'CSS3', 'JavaScript', 'PHP'],
          photo: require('../assets/portfolio/goldenDragon.png')
        },
        { section: 'UI/UX дизайн',
          name: 'Пример Landing Page',
          href: '',
          time: 'Сентрябрь, 2019',
          photo: require('../assets/portfolio/template.png')
        },
      ]
    }
  },
  methods: {
    activeWeb_sites(web, name) {
      let sites =[]
      for (let i = 0; i < web.length; i++) {
        if (name === 'Все проекты') sites.push(web[i])
        else if (web[i].section === name) sites.push(web[i])
      }
      return sites
    },
    years_now() {
      return new Date().getFullYear()
    },
  }
}
</script>

<style lang="scss">
header {
  padding: 12px 0;
  background-color: #fff;
  box-shadow: 0 6px 4px -4px rgba(0, 0, 0, 0.2);
}

a {
  font-weight: 500;
  color: inherit;
}

section {
  position: relative;
  padding: 50px 0;
  border-bottom: 1px solid #e4e4e4;
}

label {
  margin: 0;
}

footer {
  padding: 15px;
  font-size: 14px;
  background-color: #efefef;
}

hr {
  margin-top: 20px;
  margin-bottom: 20px;
  border: 0;
  border-top: 1px solid #eee;
}

.button-primary {
  min-width: 175px;
}

#hello {
  padding: 100px 0 50px 0;
}

.logo {
  font-size: 24px;
  font-weight: 500;
}

.links {
  display: flex;
  align-items: center;
  font-size: 13px;
  color: inherit;
  text-transform: uppercase;
}

.me_button {
  width: 45%;
  min-width: 175px;
  height: 50px;
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
  border-radius: 0 !important;
}

.first_text {
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
}

.second_text {
  font-size: 14px;
}

.block_left,
.block_right {
  height: 100%;
}

.zigzag {
  position: absolute;
  bottom: 10px;
  left: 15px;
  width: 105px;
}

.st1 {
  fill: none;
  stroke-miterlimit: 10;
  stroke-width: 7px;
}

.contact_form {
  &__name {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;

    input {
      height: 50px;
      padding: 10px;
      border: 2px solid #e4e4e4;
      outline: 0;
      transition: 0.3s;
    }

    input:focus,
    input:hover {
      border: 2px solid #007bff;
      outline: 0;
      transition: 0.3s;
    }
  }

  textarea {
    padding: 10px;
    border: 2px solid #e4e4e4;
    outline: 0;
    transition: 0.3s;
  }

  textarea:focus,
  textarea:hover {
    border: 2px solid #007bff;
    outline: 0;
    transition: 0.3s;
  }
}

.block_content {
  padding-bottom: 55px;
}
</style>

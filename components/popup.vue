<template>
  <div class="popup" v-on:click.self="closePopup()">
    <div class="popup__container" >
      <b-container>
        <b-row>
          <b-col cols="12">
            <h1 class="mb-4">{{ portfolio_data.name }}<span class="text-primary">.</span></h1>
            <h3>Дата: <span>{{ portfolio_data.time }}</span></h3>
            <h3>Описание:</h3>
            <p class="text-secondary">
              {{ portfolio_data.desc }}
            </p>
            <h3>Технологии:</h3>
            <ul>
              <li v-for="item in portfolio_data.technology" :key="item.id">
                <span>{{ item }}</span>
              </li>
            </ul>
            <h3>Тип разработки: <span>{{ portfolio_data.type }}</span></h3>
            <div v-if="portfolio_data.type === 'CMS'">
              <h3>Движок:</h3>
              <p>{{ portfolio_data.type_engine }} {{ portfolio_data.version_engine }}</p>
            </div>
            <div v-if="portfolio_data.type_engine === 'Wordpress'">
              <h3>Модули:</h3>
              <ul>
                <li v-for="item in portfolio_data.modules" :key="item.id">
                  <span>{{ item }}</span>
                </li>
              </ul>
            </div>
            <h3>Общий вид:</h3>
            <div>
              <img width="100%"
                   :key="portfolio_data.id"
                   :src="portfolio_data.photo"
                   :alt="portfolio_data.name"
                   style="object-fit: cover;">
            </div>
          </b-col>
          <b-col cols="12">
            <div class="d-flex justify-content-between mt-4 button_body flex-wrap">
              <b-button
                v-if="portfolio_data.href !== ''"
                variant="primary"
                class="me_button d-flex align-items-center justify-content-center w-100 mt-2"
                :href="portfolio_data.href"
                target="_blank">Посетить сайт</b-button>
              <b-button
                v-else
                variant="primary"
                class="me_button d-flex align-items-center justify-content-center"
                target="_blank">Шаблон страницы</b-button>
              <b-button variant="outline-secondary" class="me_button w-100 mt-2" @click="closePopup">Закрыть вкладку</b-button>
            </div>
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
export default {
  name: "popup",
  props: {
    portfolio_data: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  data (){
    return {
      isActive: false
    }
  },
  methods: {
    closePopup () {
      this.$emit('closePopup')
    }
  }
}
</script>

<style scoped lang="scss">
@media screen and(max-width: 800px) {
  .popup {
    &__container {
      width: 90vw;
    }
  }
}

@media screen and(min-width: 800px) {
  .popup {
    &__container {
      width: 50vw;
    }
  }
}

.popup {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 2000;
  width: 100%;
  height: 140vh;
  overflow-y: auto;
  background-color: #00000091;

  &__container {
    height: auto;
    padding: 40px 30px;
    margin: 50px auto 400px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.4);

    h3 {
      margin: 15px 0;

      span {
        font-size: 24px;
      }
    }

    li {
      color: $blue;

      span {
        color: #212529;
      }
    }
  }
}

.button_body {
  @media screen and (min-width: 770px) {
    width: 75%;
  }

  @media screen and (max-width: 770px) {
    width: 100%;
  }
}
</style>

<template>
  <section id="quiz-list-element" class="card">
    <div class="card-image">
      <figure class="image is-16by9">
        <router-link :to="'/quiz/' + quiz.id">
          <img v-bind:src="quiz.promo" alt=""/>
        </router-link>
      </figure>
    </div>

    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ quiz.name }}</p>
          <p class="subtitle is-6">
            <a :href="quiz.author.url">@{{ quiz.author.name }}</a>
          </p>
        </div>
      </div>

      <div class="content level">
        <div class="tags has-addons level-left">
          <span class="tag">Category</span>
          <span class="tag is-info">
            <router-link
              exact
              v-bind:to="'/category/' + quiz.category.id"
              class="has-text-light"
            >
              {{ quiz.category.name }}
            </router-link>
          </span>
        </div>
      </div>
    </div>

    <footer class="card-footer">
      <a
        :href="buildFacebookShareUrl()"
        class="card-footer-item has-text-info"
        target="_blank"
      >
        <i class="fa fa-facebook-square" aria-hidden="true"></i>
        &nbsp;Share
      </a>

      <router-link
        :to="'/quiz/' + quiz.id + '/ranking'"
        class="card-footer-item"
      >
        <i class="fa fa-bars" aria-hidden="true"></i>
        &nbsp;Ranking
      </router-link>

      <router-link
        :to="'/quiz/' + quiz.id"
        class="card-footer-item has-text-danger"
      >
        Start
      </router-link>
    </footer>
  </section>
</template>

<script>
  import {QuizModel} from '../../models/quiz.model';
  import {CategoryModel} from '../../models/category.model';

  export default {
    name: 'QuizListElement',
    props: [
      'quiz'
    ],
    methods: {
      buildFacebookShareUrl() {
        return 'https://www.facebook.com/sharer/sharer.php?u=' + location.href + '/quiz/' + this.quiz.id;
      }
    }
  }
</script>

<style lang="scss" scoped>
  #quiz-list-element {
    margin: 10px;
    width: 270px;
  }
</style>

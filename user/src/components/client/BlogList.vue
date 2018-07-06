<template>
  <div class="blog__container">
    <header class="blog__container-header">
      <h2 class="blog__container-header-title">
        Hello and welcome to my blog!
      </h2>
      <p class="blog__container-header-text">
        This site was built from the ground up with Vue. Honestly it's probably a little gimpy, but, it's a continual work in progress.
        Below you'll find (hopefully) find some entries that may have to do with software engineering, or some other topic. If you don't find any entries,
        then it probably means I've broken something and am trying to fix it. Thanks for visiting!
      </p>
    </header>
    <ul class="entries__list">
      <li class="entry__title" v-for="(entry, index) in entries" :key=index>
        <p class="entry__date">{{entry.date}}</p>
        <router-link class="entry__link" :to="'/blog/posts/' + entry._id">{{entry.title}}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import mapGetters from 'vuex';

export default {
  name: 'BlogList',
  computed: {
    entries() {
      return this.$store.getters.entries;
    }
  },
  methods: {}
};
</script>

<style lang="scss" scoped>
.blog__container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.blog__container-header {
  padding: 2rem;
  width: 80%;
  border-bottom: 3px solid $primary-color;
  @media only screen and (max-width: 400px) {
    width: 95%;
  }

  &-title {
    font-size: 4rem;
    font-weight: 100;
    margin: 1rem 0;
    @media only screen and (max-width: 400px) {
      font-size: 1.8rem;
    }
  }

  &-text {
    font-size: 2rem;
    font-weight: 100;
    @media only screen and (max-width: 400px) {
      font-size: 1.3rem;
    }
  }
}

.entries__list {
  width: 100%;
  max-width: 100%;
  list-style: none;
}

.entry__title {
  padding: 2.5rem;
  font-size: 2rem;
  text-align: center;
}

.entry__date {
  font-size: 1.5rem;
}

.entry__link {
  text-decoration: none;
  color: $primary-color;
  font-size: 3rem;

  @media only screen and (max-width: 400px) {
    font-size: 2rem;
  }
}
</style>



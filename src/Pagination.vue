<template>
    <nav :class="getNavClassName()">
        <router-link :disabled="getPreDisabledAttr()" :class="'pagination-previous'" :to="normalize(urlPrefix + (formatCurrentPage - 1))">Prev</router-link>
        <router-link :disabled="getNextDisabledAttr()" :class="'pagination-next'" :to="normalize(urlPrefix + (formatCurrentPage + 1))">Next</router-link>
        <ul class="pagination-list" >
            <li v-for="item in pagingList" >
            <router-link v-if="item !== '...'" :class="getPagingClassName(item)" :to="normalize(urlPrefix + item)">{{ item }}</router-link>
            <span v-else class="pagination-ellipsis">...</span>
            </li>
        </ul>
    </nav>
</template>

<script>
import paging from './paging.js'
export default {
  name: 'vue-bulma-pagination',
  props: {
    urlPrefix: {
      type: String,
      default: '/'
    },
    currentPage: {
      type: Number,
      default: 1
    },
    lastPage: Number,
    displayPage: {
      type: Number,
      default: 4
    },
    modifiers: {
      type: String,
      default: ''
    }
  },
  methods: {
    getNavClassName () {
      var optional = ['', 'is-centered', 'is-right']
      if(['', 'is-centered', 'is-right'].indexOf(this.modifiers.trim()) >= 0){
        return 'pagination' + this.modifiers
      } else {
        console.warn(" modifiers %s is not within the options ", this.modifiers, optional,
        '\n see more detail https://github.com/vue-bulma/vue-bulma-pagination#doc')
        return 'pagination'
      }
    },
    getPagingClassName (item) {
      return this.currentPage !== item ? 'pagination-link' : 'pagination-link is-current'
    },
    getPreDisabledAttr () {
      return this.currentPage !== 1 ? null : 'disabled'
    },
    getNextDisabledAttr () {
      return this.currentPage < this.lastPage ? null : 'disabled'
    },
    normalize (path) {
      return path.replace(/\/+/g, '/')
    }
  },
  computed: {
    pagingList () {
      return paging(this.currentPage, this.lastPage, this.displayPage)
    },
    formatCurrentPage () {
      const currentPage = Number(this.currentPage)
      return currentPage > 0 ? currentPage : 1
    }
  }
}
</script>

<style >
.pagination-list {
    list-style: none;
}
.pagination-list li {
    list-style: none;
}
</style>

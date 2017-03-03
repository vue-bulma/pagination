<template>
    <nav class="pagination">
        <router-link :class="getPreClassName()" :to="urlPrefix+'/'+(formatCurrentPage-1)" >Prev</router-link>
        <router-link :class="getNextClassName()" :to="urlPrefix+'/'+(formatCurrentPage+1)">Next</router-link>
        <ul class="pagination-list" >
            <li v-for="item in pagingList" >
            <router-link v-if="item !== '...'" :class=" getPagingClassName(item) " :to="urlPrefix+'/'+item">{{item}}</router-link>
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
    currentPage: {
      type: Number,
      default: 1
    },
    pageLength: Number,
    urlPrefix: {
        type:String,
        default:'/'
    },
    displayLength: {
        type: Number,
        default: 4
    }
  },
  methods: {
    getPagingClassName (item) {
      return this.currentPage !== item ? 'pagination-link' : 'pagination-link is-current'
    },
    getPreClassName () {
      return this.currentPage !== 1 ? 'pagination-previous' : 'pagination-previous is-disabled'
    },
    getNextClassName () {
      return this.currentPage < this.pageLength ? 'pagination-next' : 'pagination-next is-disabled'
    }
  },
  computed: {
    pagingList () {
      return paging(this.currentPage, this.pageLength, 4)
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
    list-style : none ;    
}
.pagination-list li {
    list-style : none ;
}
</style>

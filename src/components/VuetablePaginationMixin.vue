<script>
export default {
  props: {
    css: {
      type: Object,
      default () {
        return {
          wrapperClass: 'ui right floated pagination menu',
          activeClass: 'active large',
          disabledClass: 'disabled',
          pageClass: 'item',
          linkClass: 'icon item',
          paginationClass: 'ui bottom attached segment grid',
          paginationInfoClass: 'left floated left aligned six wide column'
        }
      }
    },
    icons: {
      type: Object,
      default () {
        return {
          first: 'angle double left icon',
          prev: 'left chevron icon',
          next: 'right chevron icon',
          last: 'angle double right icon'
        }
      }
    },
    onEachSide: {
      type: Number,
      default () {
        return 2
      }
    }
  },
  data: function () {
    return {
      tablePagination: null
    }
  },
  computed: {
    totalPage () {
      return this.tablePagination === null
        ? 0
        : this.tablePagination.totalPages
    },
    isOnFirstPage () {
      return this.tablePagination === null
        ? false
        : this.tablePagination.first
    },
    isOnLastPage () {
      return this.tablePagination === null
        ? false
        : this.tablePagination.last
    },
    notEnoughPages () {
      return this.totalPage < (this.onEachSide * 2) + 4
    },
    windowSize () {
      return this.onEachSide * 2 + 1
    },
    windowStart () {
      if (!this.tablePagination || this.tablePagination.number <= this.onEachSide) {
        return 0
      } else if (this.tablePagination.number >= (this.totalPage - this.onEachSide)) {
        return this.totalPage - 1 - this.onEachSide * 2
      }

      return this.tablePagination.number - this.onEachSide
    }
  },
  methods: {
    loadPage (page) {
      this.$emit('vuetable-pagination:change-page', page)
    },
    isCurrentPage (page) {
      return page === this.tablePagination.number
    },
    setPaginationData (tablePagination) {
      this.tablePagination = tablePagination
      this.tablePagination.from = this.tablePagination.number * this.tablePagination.size + 1
      this.tablePagination.to = this.tablePagination.from + this.tablePagination.numberOfElements - 1
    }
  }
}
</script>

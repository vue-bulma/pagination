# Pagination

Pagination component for Vue Bulma.

## Installation

```sh
$ npm install vue-bulma-pagination --save
or
$ yarn add vue-bulma-pagination --save
```

## Examples

```vue
<template>
  <div>
    <pagination urlPrefix='/' currentPage=2 pageLength=100 /> 
  </div>
</template>

<script>
import Pagination from 'vue-bulma-pagination'

export default {
  components: {
    Pagination
  }
}
</script>
```
## doc

|  porps    |   required   |   default   |  desc |
| ---- | ---- | ---- | ---- |
|  urlPrefix    |  false    |   '/'   |  urlPrefix for vue-router  |
|  currentPage   |   true   |      |    |
|  pageLength  |   false   |   4   |  total pageLength  |
|  displayLength  |   false   |   4   |  how many page number will to display |


## Badges

![](https://img.shields.io/badge/license-MIT-blue.svg)
![](https://img.shields.io/badge/status-dev-yellow.svg)

---

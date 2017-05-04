# Pagination

Pagination component for Vue Bulma.

## Installation

```sh
$ npm install vue-bulma-pagination --save
# or
$ yarn add vue-bulma-pagination --save
```

## Examples

```vue
<template>
  <div>
    <pagination :urlPrefix="'/'" :currentPage="2" :lastPage="100" /> 
  </div>
</template>

<script>
import Pagination from 'vue-bulma-pagination/src/Pagination'

export default {
  components: {
    Pagination
  }
}
</script>
```
## Document

| props       | required | default | optional                    | desc                             |
| ----------- | -------- | ------- | --------------------------- | -------------------------------- |
| urlPrefix   | `false`  | '/'     |                             | urlPrefix for vue-router         |
| currentPage | `true`   | 1       |                             |                                  |
| lastPage    | `true`   |         |                             | the last page number             |
| displayPage | `false`  | 4       |                             | page number will to be displayed |
| modifiers   | `false`  | ''      | '','is-centered','is-right' |                                  |
| prev        | `false`  | ''      | Prev                        | text of `prev` button            |
| next        | `false`  | ''      | Next                        | text of `next` button            |


## Badges

![](https://img.shields.io/badge/license-MIT-blue.svg)
![](https://img.shields.io/badge/status-dev-yellow.svg)

---

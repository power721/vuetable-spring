# Vuetable-spring - data table simplify!

### Vuetable-spring works with Vue 2.x

This is a fork version of [Vuetable-2](https://github.com/ratiw/vuetable-2).

Changes:

* Use spring pageable structure by default.
```json
{
  "content" : [],
  "last" : false,
  "totalPages" : 4,
  "totalElements" : 17,
  "sort" : [ {
    "direction" : "DESC",
    "property" : "id",
    "ignoreCase" : false,
    "nullHandling" : "NATIVE",
    "ascending" : false
  } ],
  "numberOfElements" : 5,
  "first" : false,
  "size" : 5,
  "number" : 2
}
```
* Support template in fields.
```js
fields: [
    {
      name: 'id'
    },
    {
      name: 'name', 
      template: '<router-link :to="\'/users/\' + rowData.id">{{ value }}</router-link>'
  }]
```
* Sortable by default.

---

### Documentation and Tutorial

Documentation is still under development. Meanwhile, check out the [Tutorial](https://github.com/ratiw/vuetable-2-tutorial/blob/master/doc/README.md)
with follow-along project [here](https://github.com/ratiw/vuetable-2-tutorial). It should be enough to get you started.

If you've been using Vuetable for Vue 1.x before, checkout [what's changed](https://github.com/ratiw/vuetable-2/blob/master/changes.md) for info on changes from Vuetable for Vue 1.x and the [upgrade guide](https://github.com/ratiw/vuetable-2/blob/master/upgrade-guide.md) on how you could upgrade from Vuetable for Vue 1.x.


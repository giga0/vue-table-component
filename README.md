# vue-table-component

### Demo
###### CodeSandbox: https://codesandbox.io/s/github/giga0/vue-table-component
###### Full screen: https://wy1jw67057.codesandbox.io/

### Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Introduction
This is component made in Vue.js. Everything inside is written in vanilla JS and styles are in scss.

Table component is made to render various data passed through props, allowing several functionalities like: sorting data, selecting and deselecting items, ability to emit several events to parent (sort, select and action events).

There is several props that can be passed to Table component defining it appearance and functionality:

| Prop | Required | Type | Default value | Additional info |
| ------ | ------ | ------ | ------ | ------ |
| value | true | Array (of Objects) | none | data rendered or if empty noValueMsg is rendered |
| columns | true | Array (of Objects) | none | crucial for rendering table and header above it |
| columns[i].column | true | String | none | needs to be equal to keys of objects inside Array that are sent through value prop |
| columns[i].title | false | String | columns[i].column | title for a header column |
| columns[i].sortable | false | Boolean | false | determines if it'll be possible to sort column |
| columns[i].size | false | Number | none | represent width of a column in % relative to header as a parent |
| actions | false | Array (of Objects) | none | determines if actions column will be available |
| actions[i].action | true | String | none | describes the action and will be used (as text) if icon is not defined |
| actions[i].icon | false | Object | none | icon for specified action |
| actions[i].access | false | Function | () => true | function that determines access for specified action |
| selection | false | Array (of Objects) | none | represent selected data Objects of value Array |
| sortData | false | Object | none | represent params used for sorting |
| sortData.key | false | String | none | represent sortable column |
| sortData.order | false | String | none | represent sort order |
| maxHeight | false | String | 100% | determines height of table-list |
| noValueMsg | false | String | No data available | displayed if value Array is empty |

# Part 1: Playing with Vue.js syntax

## Step 1: print a single question

You should be able to see a first question.

* bind each values to the DOM:
  * For text data binding, use the curly braces (aka mustaches) syntax {% raw %}`{{ object.property }}`{% endraw %}
  * We can also put expression inside Mustaches like the following {% raw %}`{{ new Date(object.date*1000).toLocaleDateString() }}`{% endraw %}
  * Mustaches cannot be used inside HTML attributes. Instead use a v-bind directive: `v-bind:href="obj.mylink"` or the shorthand: `:href="obj.mylink"`
  * Only show the view answer button if `is_answered` is set to true (use [`v-if`](https://vuejs.org/v2/guide/conditional.html#v-if))
  * to print tags, you have to use [`v-for`](https://vuejs.org/v2/guide/list.html#Mapping-an-Array-to-Elements-with-v-for)

## Step 2: print a list of questions

Once everything is set, use the second dataset as datas (multiple instead of single)

```js
import questions from '../api/stackoverflow-search-multiple.json'
// ...
data () {
  return {
    questions: questions.items
  }
}
```

You should use the `v-for` directive to loop the questions.

## Solution

See: https://github.com/maxpou-slides/vue-workshop-app/compare/step-0...step-1

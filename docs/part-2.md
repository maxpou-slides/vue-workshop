# Part 2: Component everywhere!

## Step 1: file separation

1. Rename `HelloWorld.vue` by `QuestionList.vue`. Don't forget to update the router file too!
2. Create a new file `QuestionListItem.vue` and put inside the `<div class="comment">` from the previous file.


## Step 2: passing properties to subcomponents

Here's how to pass properties between 2 components parent-child where TodoList represent the parent and TodoListItem represent the childrens.

* QuestionList.vue

    ```html
    <template>
      <div class="ui container">
        <div class="ui comments" v-for="question in questions" :key="question.question_id">
          <question-list-item :question="question" />
        </div>
      </div>
    </template>

    <script>
    import QuestionListItem from './QuestionListItem'

    export default {
      name: 'QuestionList',
      components: {
        QuestionListItem
      },
      data () {
        return {
          todos: {
            /* ... */
          }
        }
      }
    }
    </script>
    ```


* QuestionListItem.vue

    ```html
    <template>
      <!-- content -->
    </template>

    <script>
    export default {
      name: 'QuestionListItem',
      props: {
        todo: {
          type: Object
        }
      }
    }
    </script>
    ```

## Solution

See: https://github.com/maxpou-slides/vue-workshop-app/compare/step-1...step-2
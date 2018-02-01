# Part 2: Component everywhere!

## Step 1: file separation

1. Rename `HelloWorld.vue` by `QuestionList.vue`. Don't forget to update the router file too!
2. Create a new file `QuestionListItem.vue` and put inside the `<div class="comment">` from the previous file.


## Step 2: passing properties to subcomponents

Here's how to pass properties between 2 components parent-child where TodoList represent the parent and TodoListItem represent the childrens.

* TodoList.vue

    ```html
    <template>
      <div class="ui container">
        <div class="ui todos" v-for="todo in todos" :key="question.question_id">
          <todo-list-item :todo="todo" />
        </div>
      </div>
    </template>

    <script>
    import TodoList from './QuestionListItem'

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


* TodoListItem.vue

    ```html
    <template>
      <p>{{ todo.content }}</p>
    </template>

    <script>
    export default {
      name: 'TodoListItem',
      props: {
        todo: {
          type: Object
        }
      }
    }
    </script>
    ```
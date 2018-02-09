# Part 4: Routing

## Step 1: create a new component: AnsweredQuestion

1. Create a `AnsweredQuestion.vue` component with the following content:
  ```html
  {% raw %}
  <template>
    <div class="ui container">
      <div class="ui items">
        <div class="item">
          <div class="image">
            <img :src="question.owner.profile_image">
          </div>
          <div class="content">
            <a class="header">{{ question.title }}</a>
            <div class="meta">
              <span>{{ new Date(question.creation_date*1000).toLocaleDateString() }}</span>
            </div>
            <div class="description" v-html="question.body" />
          </div>
        </div>
      </div>
      <hr>
      <div class="ui comments" v-for="answer in answers" :key="answer.answer_id">
        <div class="comment">
          <a class="avatar">
            <img :src="answer.owner.profile_image">
          </a>
          <div class="content">
            <a class="author">{{ answer.owner.display_name }}</a>
            <div class="metadata">
              <div class="date">{{ new Date(answer.creation_date*1000).toLocaleDateString() }}</div>
              <div class="rating">
                <i class="star icon"></i>
                {{ answer.score }} votes
              </div>
              <div v-if="answer.is_accepted" class="ui green label">
                <i class="checkmark icon"></i> Accepted
              </div>
            </div>
            <div class="text" v-html="answer.body">
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>

  <script>
  import { getQuestion, getAnswers } from '../api/questions'

  export default {
    name: 'AnsweredQuestion',
    data () {
      return {
        question: {},
        answers: []
      }
    },
    mounted () {
      getQuestion(this.$route.params.questionId).then(response => {
        this.question = response.data.items[0]
      })
      getAnswers(this.$route.params.questionId).then(response => {
        this.answers = response.data.items.sort((a, b) => b.score - a.score)
      })
    }
  }
  </script>

  <style scoped>
  * >>> pre {
    padding: 16px;
    overflow: auto;
    font-size: 85%;
    line-height: 1.45;
    background-color: #f6f8fa;
    border-radius: 3px;
  }

  * >>> *:not(pre) > code {
    background-color: #f6f8fa;
    border-radius: 3px;
    padding: 3px;
    font-size: 85%;
  }
  </style>
  {% endraw %}
  ```

2. Don't only copy / paste the previous code, but try to understand it.
  * `<div v-html="question.body"><div>`: it means, put this value as the html of the div
  * *style scoped*: When a `<style>` tag has the scoped attribute, its CSS will apply to elements of the current component only!

3. The previous file require 2 new functions `getQuestion()` and `getAnswers()`. Add them in the `api\questions.js`:
  ```js
  /**
    * @param {number} question id
    * @return {Promise<Object>} List of answers
    * @see {@link https://api.stackexchange.com/docs/answers-on-questions#order=desc&sort=activity&ids=30877491&filter=!9Z(-wzu0T&site=stackoverflow&run=true}
    * @see {@link https://api.stackexchange.com/docs/types/answer}
    */
  export function getAnswers (id) {
    return axios.get(`${process.env.API_URL}questions/${id}/answers?order=desc&sort=activity&site=stackoverflow&filter=!9Z(-wzu0T`)
  }

  /**
    * @param {number} question id
    * @return {Promise<Object>} Question
    * @see {@link https://api.stackexchange.com/docs/questions-by-ids#order=desc&sort=activity&ids=30877491&filter=!-*jbN-o9Aeie&site=stackoverflow&run=true}
    * @see {@link https://api.stackexchange.com/docs/types/question}
    */
  export function getQuestion (id) {
    return axios.get(`${process.env.API_URL}questions/${id}?order=desc&sort=activity&site=stackoverflow&filter=!-*jbN-o9Aeie`)
  }
  ```

## Routing

1. Now in the router (router/index.js), add a new route for this view. Variables in the path looks like this: `path: 'questions/:id'`
2. Now, we have to link the two views. In `QuestionListItem.vue`, we have to adapt the `View answers` by using the [`<router-link>`](https://router.vuejs.org/en/api/router-link.html).
  ```html
  <router-link :to="{ name: 'RouteName', params: { paramName: 42 }}">I'm a link</router-link>
  ```

🎉 Tadaaa, you are now able to navigate between the question list and the answers!


## Solution

See: https://github.com/maxpou-slides/vue-workshop-app/compare/step-3...step-4
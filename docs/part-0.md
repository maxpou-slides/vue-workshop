# Part 0: Scaffolding

## Step 1: Initialize the app

1. Install 
  ```bash
  # Install vue-cli
  $ npm install -g vue-cli

  # Scaffold project
  $ vue init webpack vue-workshop-app

  ? Project name vue-workshop-app
  ? Project description A Vue.js project
  ? Author Maxence POUTORD <maxence.poutord@gmail.com>
  ? Vue build standalone
  ? Install vue-router? Yes
  ? Use ESLint to lint your code? Yes
  ? Pick an ESLint preset Standard
  ? Set up unit tests No
  ? Setup e2e tests with Nightwatch? No
  ? Should we run `npm install` for you after the project has been created? (recommended) npm
  ```

2. Add css framework in the `index.html`
  ```html
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.2.14/semantic.min.css">
  ```

3. Test if everything works fine
  ```bash
  $ cd vue-workshop-app
  $ npm install
  $ npm run dev

  DONE  Compiled successfully in 2574ms
  I  Your application is running here: http://localhost:8080
  ```

## Step 2: Now let's prepare everything for the first step


1. Open `src\App.vue` and replace the content by the following
  ```html
  <template>
    <div id="app">
      <h1 class="ui center aligned header">StackOverVue</h1>
      <router-view/>
    </div>
  </template>

  <script>
  export default {
    name: 'App'
  }
  </script>

  <style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    margin-top: 60px;
  }
  </style>
  ```
2. Create a new file `src\api\stackoverflow-search-single.json` with the following content: https://api.stackexchange.com/2.2/search?order=desc&sort=votes&intitle=vue&site=stackoverflow
3. Open `src\components\HelloWorld.vue` and replace the content by the following
  ```html
  <template>
    <div class="ui container">
      <div class="ui comments">
        <div class="comment">
          <a class="avatar">
            <img src="https://semantic-ui.com/images/avatar/small/stevie.jpg">
          </a>
          <div class="content">
            <a class="author">John Doe</a>
            <div class="metadata">
              <div>1 april 2017</div>
              <div><i class="star icon"></i>1000 Votes</div>
              <div><i class="comment icon"></i>5 answers</div>
            </div>
            <div class="ui mini label">Vue.js</div>
            <div class="text">
              Hey guys, how do you bind data to the DOM?
            </div>
            <div class="actions">
              <a>View answers</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>

  <script>
  export default {
    name: 'HelloWorld',
    data () {
      return {
        question: {
          tags: ['javascript', 'vue.js', 'vue-resource', 'vuex'],
          owner: {
            reputation: 3410,
            user_id: 2294225,
            user_type: 'registered',
            accept_rate: 92,
            profile_image: 'https://i.stack.imgur.com/07yK6.jpg?s=128&g=1',
            display_name: 'Stephan-v',
            link: 'https://stackoverflow.com/users/2294225/stephan-v'
          },
          is_answered: true,
          view_count: 5252,
          accepted_answer_id: 38074979,
          answer_count: 1,
          score: 14,
          last_activity_date: 1467114417,
          creation_date: 1467106122,
          last_edit_date: 1467114417,
          question_id: 38072302,
          link: 'https://stackoverflow.com/questions/38072302/structuring-a-vue-vuex-project',
          title: 'Structuring a Vue + Vuex project'
        }
      }
    }
  }
  </script>
  ```
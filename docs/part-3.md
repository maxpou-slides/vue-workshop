# Part 4: HTTP

## Step 1: Load data on mounting

1. Implement the `mounted()` method and fill data with the JSON file *(as before)*.
Mounted function looks like this:

```js
export default {
  name: 'MyComponent',
  data () {
    return {
      awesomeDatas: []
    }
  },
  mounted () {
    console.log('Hey, I just get mounted!')
    this.awesomeDatas = ['bim', 'bam', 'bingo']
  }
}
```

## Step 2: from static JSON file to HTTP GET

1. Install axios: `npm i axios`
2. Create a environment variable API_URL in the `config/prod.env.js` like the following `API_URL: '"https://api.stackexchange.com/2.2/"'`
3. Create the file `api/questions.js` wich gonna contain all api calls dedicated to 'questions'
  ```js
  // api/questions.js
  import axios from 'axios'

  /**
   * @param {string="vue"} search
   * @return {Promise<Object>} List of questions
   * @see {@link https://api.stackexchange.com/docs/search}
   * @see {@link https://api.stackexchange.com/docs/types/question}
   */
  export function searchQuestions (search = 'vue') {
    return axios.get(`${process.env.API_URL}search?order=desc&sort=votes&intitle=${search}&site=stackoverflow`)
  }
  ```
4. adapt code in `QuestionList.vue`
  ```js
  mounted () {
    searchQuestions('vue').then(response => {
      this.questions = response.data.items
    })
  }
  ```
Now the component's `question` default property should be an empty array.
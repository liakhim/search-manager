<template>
  <div class="container">
    <div class="search-wrapper">
      <input type="text" v-model="search" placeholder="Search title.."/>
      <button @click="search = ''" class="standard-button-danger">Clear</button>
      <label>Search title:</label>
    </div>
    <b-container class="bv-example-row" style="margin-top: 100px">
      <b-row>
        <b-col>
          <CardQuestion :question="'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'"
                        :answer="'Lorem ipsum dolor sit amet, consectetur adipisicing elit. A ab, ducimus labore odio tempore voluptates?'"
                        :category="'Category 1'"/>
        </b-col>
        <b-col>
          <CardQuestion :question="'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'"
                             :answer="'Lorem ipsum dolor sit amet, consectetur adipisicing elit. A ab, ducimus labore odio tempore voluptates?'"
                             :category="'Category 1'"/></b-col>
        <b-col>
          <CardQuestion :question="'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'"
                        :answer="'Lorem ipsum dolor sit amet, consectetur adipisicing elit. A ab, ducimus labore odio tempore voluptates?'"
                        :category="'Category 1'"/>
        </b-col>
      </b-row>
    </b-container>
    <div class="wrapper">

    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  import CardQuestion from '../components/CardQuestion.vue'
  // class Post {
  //   constructor(title, link, author, img) {
  //     this.title = title;
  //     this.link = link;
  //     this.author = author;
  //     this.img = img;
  //   }
  // }
export default {
  name: 'Search Manager',
    components: {CardQuestion},
  props: {
    msg: String
  },
  data() {
    return {
      ax_data: [],
      search: '',
      userList: []
    }
  },
  computed: {
    filteredList() {
      return this.userList.filter(user => {
        return user.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  },
  methods: {
    getData() {
      axios.get('http://jsonplaceholder.typicode.com/users')
        .then((response) => {
          this.userList = response.data
        })
    }
  },
  created() {
    this.getData()
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  html, body {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  p, small, b, h1,h2, h3, h4, h5, h6 {
      padding: 0;
      margin: 0;
  }
  .wrapper {
    display: flex;
    max-width: 100%;
    flex-wrap: wrap;
    padding-top: 12px;
  }
  .container {
    max-width: 1320px;
    margin: auto;
  }
  .search-wrapper {
    position: fixed;
    width: 100%;
    height: 90px;
    background: #00000030;
    top: 0;
    left: 0;
  }

</style>

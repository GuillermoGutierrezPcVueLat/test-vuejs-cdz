<template>
    <div class="App container bg-light shadow">
        <header class="App-header">
          <img src="./assets/logo.png" :class="loading? 'App-logo Spin':'App-logo'" alt="logo" />
          <h1 class="App-title">
            VueJS Comments
            <span class="px-2" role="img" aria-label="Chat">
              💬
            </span>
          </h1>
        </header>
      <div class="row">
          <div class="col-4  pt-3 border-right">
            <h4>Ingresa tu comentario</h4>
            <CommentForm   @reload="reloadList"/>
          </div>
          <div class="col-8  pt-3 bg-white">
            <CommentList :key="list_reload"/>
            
          </div>
        </div>
    </div>
</template>
<script>

import CommentForm from './components/CommentForm.vue'
import CommentList from './components/CommentList.vue'


export default ({
    name: "app",
    components:{
        CommentForm,
        CommentList,
        
    }, 
    props:{
        comments: [],
        //loading: false
    }
    ,
    data(){
       return{
            list_reload: 0,
            img: "./assets/logo.svg"
        } 
    },
    methods: {
        reloadList(val) {
            console.log("entra a reload" + val);
            this.list_reload = this.list_reload + val;
        }
        
    },
    
})
</script>

<style>
.App {
    padding-top: 1rem;
    padding-bottom: 1rem;
    margin: 1rem auto;
}

.App-logo {
    height: 80px;
}

.Spin {
    animation: App-logo-spin infinite 2s linear;
}

.App-header {
    text-align: center;
    background-color: #37a6e7;
    padding: 20px;
    color: white;
    border-radius: 0.3rem;
}

.App-title {
    font-size: 1.5em;
}

.App-intro {
    font-size: large;
}

@keyframes App-logo-spin {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

.form-group {
    padding-top: 4px;
    padding-bottom: 4px;
}

.badge-success {
    background-color: green;
}



</style>
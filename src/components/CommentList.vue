<template>
    <div class="commentList">
      <h5 class="text-muted mb-4">
        <span class="badge badge-success">{{comments.length}}</span>
        Comentario
      </h5>
    <div v-for="(comment, index) in comments" :key="index">
        <Comment :usuario="comment.usuario" :comentario="comment.comentario"/>
    </div>
  </div>
</template>
<script>
import Comment from "./Comentario.vue"
import axiosInstance from "../Services/axiosConfig";

export default {
  components:
  {
    Comment
  },
  data() {
      return{
        comments: [],
        
      }
  },
  methods: {
    loadComentarios: function(){
          axiosInstance.get("api/mensajes").then(res => {
            console.log(res.data);
            console.log("entra a loadComentarios");
            this.comments=res.data;
            this.loading = false;
          })
        }
  },
  mounted() {
    this.loadComentarios();
  }
}
</script>

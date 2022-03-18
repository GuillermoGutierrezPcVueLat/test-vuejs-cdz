<template>
    <form @submit.prevent="onSubmit">
          <div className="form-group">
            <input
              @change="handleInputChange"
              v-model="comment.usuario"
              className="form-control"
              placeholder="😎 Tu nombre"
              name="usuario"
              type="text"
            />
          </div>
          <div className="form-group">
            <textarea
              @change="handleInputChange"
              v-model="comment.comentario"
              className="form-control"
              placeholder="🤬 Tu comentario"
              name="comentario"
              type="text"
              rows="5"
            />
          </div>
          {{error}}
          <div class="form-group">
            <button :disabled="loading" class="btn btn-primary" type="submit">
              Comentar &#10148;
            </button>
          </div>
        </form>
</template>
<script>

import axiosInstance from '../Services/axiosConfig';

export default ({
    data(){
        return {
            comment: {
                usuario: "",
                comentario: ""
            },
            error: "",
            loading: false,
            
        }
    },
    methods: {
        onSubmit: function (){
            console.log("entra a onSubmit", this.comment)
            if(!this.isFormValid()) {
                this.setError("Todos los campos son requeridos");
                return;
            }
            this.setError("");
            axiosInstance.post("/api/mensajes", this.comment).then(res => {
                console.log("respuesta", res.status);
                this.comment={usuario:"",comentario:""}
                
            })
            this.$emit('reload', 1)
        },
        isFormValid() {
            return this.comment.usuario !== "" && this.comment.comentario !== "";
        },
        
        setError: function(argT) {
            this.error=argT;
        },  
    }
})
</script>

<template>
    <div class="media mb-3" style="display: flex">
        <img
        class="mr-3 bg-light rounded"
        width="48"
        height="48"
        :src="'https://ui-avatars.com/api/?name= '+ usuario " />
        
        <div class="media-body p-2 shadow-sm rounded bg-light border" style="flexGrow: 1, marginLeft: '5px'">
            <h6 class="mt-0 mb-1 text-muted">{{usuario}}</h6>
            {{comentario}}
        </div>
    </div>
</template>
<script>
export default {
    props: {
        usuario: {type: String, default: ""},
        comentario: {type: String, default: ""}
    }
}
</script>

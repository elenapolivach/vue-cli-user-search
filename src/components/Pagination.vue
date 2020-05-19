<template>
    <div class="pagination-style" v-show="visible">
        <div><a href="#!" @click.prevent="$emit('prev-page')" class=" waves-effect pagination-btn"><i class="material-icons">arrow_back</i></a></div>
        <span class="pagination-page">Страница {{ current }} из {{ maxPages }}</span>
        <div><a href="#!" @click.prevent="$emit('next-page')" class="pagination-btn waves-effect"><i class="material-icons">arrow_forward</i></a></div> <br>
    </div>
</template>

<script>
export default {
    props: ['current', 'total', 'size', 'data'],
    computed: {
        maxPages() {
            return  Math.ceil(this.total/this.size);
        },
        visible() {
            if(!this.data.id){
                return false;
            } else{
                return true
            }
        }
    },
    

}
</script>
<template>
    <div class="error-block" v-if="text">Ошибка поиска: {{ this.text }}.
                Пользователь не найден!
                </div>
</template>

<script>
export default {
    data() {
        return {
            text: ''
        }
    },
    
    methods: {
        setText(value) {
            if(value){
                return this.text = value;
            }else{
                return this.text = ''
            }
        },
    }
}
</script>
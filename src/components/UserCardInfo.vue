<template>
    <div class="user-info-block">
            <img :src="data.avatar_url" class="img">
            <p class="user-info">{{data.name}}  <br>Репозитории: {{ data.public_repos }}</p>
          </div>
</template>

<script>
export default {
    props: ['data']
}
</script>
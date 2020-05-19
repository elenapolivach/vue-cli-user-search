<template>
    <ul class="repo-list">
        <li v-for="repo of repos" class="list-item" :key='repo.name'>
            <a :href="repo.html_url" target="_blank" class="link-repo">{{repo.name}}</a>
            <div class="star-icon">{{repo.stargazers_count}} &nbsp; &#9734;</div>
        </li>
    </ul>
</template>

<script>
export default {
    props: ['repos']
}
</script>
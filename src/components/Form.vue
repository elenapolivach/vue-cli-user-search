<template>
    <div class="row form">
        <form class="col form-search" @submit.prevent="init(userName)">
            <div class="input-field col s12">
                <input id="first_name2" type="text" class="validate" v-model="userName">
                <label class="active" for="first_name2">Имя пользователя</label>
            </div>
            <div class="btn-form-block">
              <button class="btn waves-effect waves-light " type="submit" name="action">Найти &nbsp; &#128270;</button>
            </div>
            <Error
            ref='error'
            />
        </form>
        <UserCard
        :data='dataName'
        :repos='filtered'
        :api='api'
        :sizePage='sizePage'
        :currentPage='currentPage'
        @next-page="nextPage"
        @prev-page="prevPage"
        />

        <Pagination 
            :size='sizePage'
            :total='dataName.public_repos'
            :current='currentPage'
            :data='dataName'
            @next-page='nextPage'
            @prev-page='prevPage'
            />
        </div>
</template>

<script>
import Error from '@/components/error.vue'
import UserCard from '@/components/UserCard.vue'
import Pagination from '@/components/Pagination.vue'


export default {
    data() {
        return {
            api: `https://api.github.com`,
            userName: '',
            urlName: '',
            urlRepos: '',
            dataName: {},
            dataRepos: [], 
            filtered: [],
            totalRepos: 0,
            sizePage: 3,
            currentPage: 1,
        }
    },
    components: {
    Error,
    UserCard,
    Pagination
   
  },
    methods: {
        init(userName) {
            this.dataName = {},
            this.dataRepos = []
            this.currentPage = 1;
            this.urlName = `/users/${userName}`
            this.urlRepos = `/users/${userName}/repos`
            this.fetchData(),
            this.fetchRepos()
            this.userName = ''
        },
        fetchData() {
            fetch(`${this.api + this.urlName}`)
            .then(result => result.json())
            .then(data => {
                this.dataName = data;
                this.$refs.error.setText(this.dataName.message);
                console.log('dataName', this.dataName)
            })
            .catch(error => console.log(error)); 
        },

        fetchRepos() {
            fetch(`${this.api + this.urlRepos + `?page=${this.currentPage}&per_page=${this.sizePage}`}`)
            .then(result => result.json())
            .then(data => {
                this.dataRepos= [...data];
                this.filtered = this.dataRepos;
                console.log('dataRepos', this.dataRepos);
            })
            .catch(error => console.log(error));
        },
        nextPage () {
        let maxPages = Math.ceil(this.dataName.public_repos/this.sizePage);
        
        if(maxPages > this.currentPage){
            this.currentPage++;
            fetch(`${this.api + this.urlRepos + `?page=${this.currentPage}&per_page=${this.sizePage}`}`)
            .then(result => result.json())
            .then(data => {
                this.dataRepos= [...data];
                this.filtered = this.dataRepos;
                console.log(this.dataRepos);
            })
                .catch(error => console.log(error));
         }else {
            return this.currentPage;
        }  
    },
    prevPage() {
        if(this.currentPage > 1){
            this.currentPage--;
            fetch(`${this.api + this.urlRepos + `?page=${this.currentPage}&per_page=${this.sizePage}`}`)
            .then(result => result.json())
            .then(data => {
            this.dataRepos= [...data];
            this.filtered = this.dataRepos;
            console.log(this.dataRepos);
        })
            .catch(error => console.log(error));
        }else {
            return this.currentPage;
        }
    },
        
    }
}
</script>


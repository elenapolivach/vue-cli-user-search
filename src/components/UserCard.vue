<template>
    <div>
        <div class="start-text" v-if="noUser()">Введите данные пользователя в окно поиска</div>
        <div v-else>
            <UserInfo 
            :data='data'
            />
            <div class="repo-block">
                <RepoFilter
                :repos='repos'
                @filter-name='filterName()'
                @filter-star='filterStar()'
                />
                <RepoList
                :repos='repos'
                />
            </div>  
        </div>
    </div>
</template>

<script>
import UserInfo from '@/components/UserCardInfo.vue'
import RepoList from '@/components/UserCardList.vue'
import RepoFilter from '@/components/UserCardFilter.vue'


export default {
  components: {
    UserInfo,
    RepoList,
    RepoFilter,
  },
  props: ['data', 'repos', 'sizePage', 'currentPage'],
  data() {
    return {
      star: false,
      name: false,
    }
  }, 
  methods: {
    noUser() {
        if(!this.data.id){
            return true;
        }else{
            return false;
        }
    },
    
    filterName(){
        if(!this.name) {
            this.name=!this.name;
            this.repos.sort((a, b) => {
                if (a.name < b.name) {
                    return -1;
                }
            })
        }else{
            this.name=!this.name;
            this.repos.sort((a, b) => {
                if (b.name < a.name) {
                    return -1;
                }
            })
        } 
    },
    filterStar(){
        if(!this.star) {
            this.star=!this.star;
            this.repos.sort((a, b) => {
                return b.stargazers_count - a.stargazers_count;
            })
        }else{
            this.star=!this.star;
            this.repos.sort((a, b) => {
                return a.stargazers_count - b.stargazers_count;
            }) 
        }
    },
  },
}
</script>
<template>
  <div id="app">
    <Form/>
    
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Form from '@/components/Form.vue'
export default {
  name: 'App',
  components: {
   Form 
  }
}
</script>

<style lang="scss">
@import '~materialize-css/dist/css/materialize.min.css';
body {
    background-color: #F5F5F5;
}
#app {
   display: flex;
    flex-direction: column;
}
.form {
  display: flex;
    flex-direction: column;
}
.form-search {
    width: 600px;
    display: flex;
    flex-direction: column;
    margin-bottom: 30px;;
}

.btn-form-block{
    display: flex;
    justify-content: center;
}

.start-text {
    text-align: center;
}

.user-info-block {
    display: flex;
    justify-content: center;
    margin-bottom: 30px;
}

.img {
    width: 150px;
    height: 150px;
    margin-right: 50px; 
    border-radius: 50%; 
    
}

.user-info {
    text-align: center;
}

.repo-block {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.repo-list {
    text-decoration: none;
}
.list-item {
    width: 600px;
    height: 50px;
    border-bottom: 1px solid rgb(180, 178, 178);
    display: flex;
    justify-content: space-between;
    padding: 0 30px;
    font-size: 20px;
    align-items: center;
}

.link-repo{
    color: black;
}

.pagination-style{
    display: flex;
    justify-content: center;
}
.pagination-btn{
    display: block;
    color:whitesmoke;
    margin: 5px 15px;
    width: 50px;
    height: 30px;
    border: 1px solid transparent;
    text-align: center;
    line-height: 30px;
    border-radius: 15px;
    background-color: #26a69a;
}

.pagination-page {
    line-height: 35px;
}

.pagination-btn:hover{
   opacity: 0.8;
}

.error-block{
    display: flex;
    justify-content: center;
    padding-top: 20px;
}
.btn-filtered-block {
    width: 600px;
    display: flex;
    justify-content: space-between;
}
.btn-filter{
    border: none;
    background-color: #F5F5F5;
    margin-left: 20px;
    margin-right: 20px;
    text-decoration: none;
    color: black;
}
.btn-filter:hover {
    opacity: 0.8;
}

</style>

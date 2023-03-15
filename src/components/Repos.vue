<script>
    export default {
        data() {
            return {
                data: [],
                currentPage: 1,
                view: ""
            }
        },
        methods: {
            showMore: function() {
                this.currentPage += 1
                // console.log(this.currentPage)
            }
        },
        mounted() {
            fetch(`https://api.github.com/users/mbonamensa/repos?per_page=6&page=${this.currentPage}`, {
                headers: {
                    Accept: "application/json"
                },
            }) 
            .then((res) => res.json()) 
            // .then((data) => (this.data = data))
            .then((data) => {
                if (data.length === 0) {
                    this.view = "End of Repos"
                }else {
                    this.view = "View More"
                    this.data = [...this.data, ...data]
                    console.log(this.currentPage)
                }
            })
        }
        
    }
</script>

<template>
    <div class="repo-container">   
        <div v-for="repo in data" class="repo-card" :key="repo.id">
            <router-link :to="`/details/${repo.name}`"><h2 class="repo-name">{{ repo.name }}</h2></router-link>
            <p class="language">Langauge: {{ repo.language }}</p>
            <p class="date">Start date & time: {{ repo.created_at }}</p>
            <p class="visibility">Visibility: {{ repo.visibility }}</p>
        </div>
    </div>
    <p class="view-more" @click="showMore">{{ view }}</p>
  
</template>


<style>

.repo-container {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(300px,1fr));
    grid-gap: 30px;
    width: 90%;
    margin: 0 auto;
    margin-bottom: 5rem;
}

.repo-card,
.repodetail-card {
    border: 1px solid #00bd7e;
    padding: 13px;
    border-radius: 5px;
}


.repo-name {
    color: #00bd7e;
    font-size: 2rem;
    word-break: break-word;
}

p {
    padding: 5px 0;
}

</style>
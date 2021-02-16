<template>
    <div class="container">
         <select v-model="newsType" @change="changeType">
             <option value="story">Story</option>
             <option value="poll">Pool</option>
        </select>
        <div v-for="(item, index) in list" :key="index">
            <p>Author: {{ item.author }}</p>
        </div>
        <infinite-loading :identifier="infiniteId" @infinite="infiniteHandler"></infinite-loading>
    </div>
</template>
<script>
import InfiniteLoading from 'vue-infinite-loading';
import axios from 'axios';
export default {
    components: {
        InfiniteLoading
    },
    data() {
        return {
            page: 1,
            list: [],
            newsType: 'story',
            infiniteId: +new Date()
        }
    },
    methods: {
        infiniteHandler($state) {
            axios.get('//hn.algolia.com/api/v1/search_by_date', {
                params: {
                    page: this.page,
                    tags: this.newsType
                }
            }).then(({data}) => {
                if(data.hits.length) {
                    this.page += 1;
                    this.list.push(...data.hits);
                    $state.loaded();
                } else {
                    $state.complete()
                }
            })
        },
        changeType() {
            this.page = 1;
            this.list = [],
            this.infiniteId += 1
        }
    }
}
</script>
<style>
.container {
    height: 400px;
}
</style>
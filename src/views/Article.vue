<template>
    <div class="container">
        <div class="row">
            <div class="col-md-10 offset-md-1">
                <div class="card" v-if="!loading">
                    <img height="420px;" :src="article.imageUrl" alt="" class="card-img-top">
                    <div class="card-body">
                        <div class="div.card-title text-center my-3"> {{ article.title }} </div>
                        <div class="article-content" v-html="article.content"></div>

                        <div class="comments my-4">
                            <vue-disqus shortname="community-blog" :identifier="article.slug" :url="`http://localhost:8080/article/${article.slug}`"></vue-disqus>
                        </div>
                    </div>
                </div>
                <div class="loader text-center" v-else>
                    <i class="fas fa-5x fa-spin fa-spinner"></i>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Axios from 'axios';
import config from '@/config';

export default {
    mounted() {
        this.getArticle();
    },
    data() {
        return {
            article: {},
            loading: true,
        }
    },
    methods: {
        getArticle() {
            Axios.get(`${config.apiUrl}/article/${this.$route.params.id}`).then(response => {
                this.loading = false;
                this.article = response.data.data;
            });
        }
    }
}
</script>

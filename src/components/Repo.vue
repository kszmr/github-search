<template>
    <div class="card card-body mb-2">
        <div class="row">
            <div class="col-md-6">
                <a class="text-dark" href="repo.html_url" target="_blank">{{ repo. name }}</a>
            </div>
            <div class="col-md-6">
                <span style="margin-right: 0.2em;" class="badge badge-warning">Stars: {{ repo.stargazers_count }} </span>
                <span style="margin-right: 0.2em;" class="badge badge-info">Watch: {{ repo.watchers_count }} </span>
                <span style="margin-right: 0.2em;" class="badge badge-secondary">Forks: {{ repo. forks_count }}</span>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ["repo"]
};
</script>
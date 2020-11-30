<template>
    <div>
        <div class="col-md-4">
                <div class="card" style="width: 18rem;">
                <img alt="" class="card-img-top" :src="user.avatar_url">
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">Repositories: <span class="badge badge-success">{{ user.public_repos }}</span></li>
                    <li class="list-group-item">Followers: <span class="badge badge-success">{{ user.followers }}</span></li>
                    <li class="list-group-item">Following: <span class="badge badge-success">{{ user.following }}</span></li>
                </ul>
                <div class="card-body">
                    <a :href="url" target="blank" class="btn btn-dark btn-block">See profile</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["user"],
        data() {
            return { 
                url: `https://github.com/${this.user.login}`
            }
        }
};
</script>
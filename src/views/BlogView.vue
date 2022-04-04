<template>
  <!-- Page header with logo and tagline-->
  <header class="py-5 bg-light border-bottom mb-4">
    <div class="container">
      <div class="text-center my-5">
        <h1 class="fw-bolder">Welcome to Blog Home!</h1>
        <p class="lead mb-0">
          A Bootstrap 5 starter layout for your next blog homepage
        </p>
      </div>
    </div>
  </header>
  <!-- Page content-->
  <div class="container">
    <div class="row">
      <!-- Blog entries-->
      <div class="col-lg-8">
        <!-- Featured blog post-->
        <div class="card mb-4">
          <a href="single.html"
            ><img
              class="card-img-top"
              src="https://dummyimage.com/850x350/dee2e6/6c757d.jpg"
              alt="..."
          /></a>
          <div class="card-body">
            <div class="small text-muted">January 1, 2022</div>
            <h2 class="card-title">Featured Post Title</h2>
            <p class="card-text">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit.
              Reiciendis aliquid atque, nulla? Quos cum ex quis soluta, a
              laboriosam. Dicta expedita corporis animi vero voluptate
              voluptatibus possimus, veniam magni quis!
            </p>
            <router-link class="btn btn-primary" to="/singl"
              >Read more →</router-link
            >
          </div>
        </div>
        <!-- Nested row for non-featured blog posts-->
        <div
          class="row col-sm-12 col-md-6 col-lg-4"
          v-for="post in posts"
          :key="post"
        >
          <!--  Start Demo Post DIV  -->
          <div class="col">
            <div class="card shadow-sm">
              <img
                src="https://via.placeholder.com/200.png/09f/fff"
                alt="placeholder"
              />
              <div class="card-body">
                <p class="card-text">{{ post.body }}</p>
                <div class="d-flex justify-content-between align-items-center">
                  <div class="btn-group">
                    <button
                      type="button"
                      class="btn btn-sm btn-outline-secondary"
                    >
                      View
                    </button>
                    <button
                      type="button"
                      class="btn btn-sm btn-outline-secondary"
                    >
                      Edit
                    </button>
                  </div>
                  <small class="text-muted">9 mins</small>
                </div>
              </div>
            </div>
          </div>
          <!--  End Demo Post DIV  -->
        </div>
        <!-- Pagination-->
        <nav aria-label="Pagination">
          <hr class="my-0" />
          <ul class="pagination justify-content-center my-4">
            <li class="page-item disabled">
              <a class="page-link" href="#" tabindex="-1" aria-disabled="true"
                >Newer</a
              >
            </li>
            <li class="page-item active" aria-current="page">
              <a class="page-link" href="#!">1</a>
            </li>
            <li class="page-item"><a class="page-link" href="#!">2</a></li>
            <li class="page-item"><a class="page-link" href="#!">3</a></li>
            <li class="page-item disabled">
              <a class="page-link" href="#!">...</a>
            </li>
            <li class="page-item"><a class="page-link" href="#!">15</a></li>
            <li class="page-item"><a class="page-link" href="#!">Older</a></li>
          </ul>
        </nav>
      </div>
      <!-- Side widgets-->
      <div class="col-lg-4">
        <!-- Search widget-->
        <div class="card mb-4">
          <div class="card-header">Search</div>
          <div class="card-body">
            <div class="input-group">
              <input
                class="form-control"
                type="text"
                placeholder="Enter search term..."
                aria-label="Enter search term..."
                aria-describedby="button-search"
              />
              <button class="btn btn-primary" id="button-search" type="button">
                Go!
              </button>
            </div>
          </div>
        </div>
        <!-- Categories widget-->
        <div class="card mb-4">
          <div class="card-header">Categories</div>
          <div class="card-body">
            <div class="row">
              <div class="col-sm-6">
                <ul class="list-unstyled mb-0">
                  <li><a href="#!">Web Design</a></li>
                  <li><a href="#!">HTML</a></li>
                  <li><a href="#!">Freebies</a></li>
                </ul>
              </div>
              <div class="col-sm-6">
                <ul class="list-unstyled mb-0">
                  <li><a href="#!">JavaScript</a></li>
                  <li><a href="#!">CSS</a></li>
                  <li><a href="#!">Tutorials</a></li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <!-- Side widget-->
        <div class="card mb-4">
          <div class="card-header">Side Widget</div>
          <div class="card-body">
            You can put anything you want inside of these side widgets. They are
            easy to use, and feature the Bootstrap 5 card component!
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import MainPosts from "@/components/MainPosts.vue";
export default {
  name: "BlogPage",
  data: () => {
    return {
      posts: [],
    };
  },
  mounted: function () {
    this.axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then((response) => {
        console.log(response.data[0].title);
        this.posts = response.data;
      });
  },
};
</script>

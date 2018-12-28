<template>
  <div class="footer">
    <div class="copyright">
      <p>&copy 2018</p>
      <a href="https://github.com/DanSimonson/view-quote" target="_blank" aria-label="Facebook">
        <i class="fab fa-github fa-lg">See Code In GitHub Repository</i>
      </a>
      <h4>
        made with
        <i class="fas fa-heart fa-sm"></i>
        <a href="https://mariposaweb.net" target="_blank">@mariposaweb.net</a>
      </h4>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  }
};
</script>
<style scoped lang='scss'>
@import "../../public/styles.scss";

.footer {
  /*position: fixed;
        left: 0;
        bottom: 0;
        width: 100%;*/
  background-color: #00b6f1;
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
}

.copyright {
  display: flex;
  align-items: center;
  justify-content: space-around;
  padding: 10px;
  color: $Black;

  a {
    margin-right: 10px;
    color: #8b9dc3;
  }

  a:hover,
  a:active {
    color: #3b5998;
  }

  h4 {
    font-size: 1rem;

    a {
      text-decoration: none;
      color: $Black;
      transition: all 0.3s;
    }

    a:hover,
    a:active {
      color: #cccccc; /*#c91517;*/
    }
  }

  .fas.fa-heart {
    color: red;
  }

  i.fab.fa-github {
    color: #040204; /*#3b5998;*/
    cursor: pointer;
    transition: all 0.3s;
  }

  i.fab.fa-github:hover {
    color: #cccccc; /*#8b9dc3;*/
  }

  p {
    font-size: 1rem;
    /*margin-left: 10px;*/
  }
}

@media (max-width: 700px) {
  /*.copyright {
            flex-direction: column;
        }*/
}
</style>
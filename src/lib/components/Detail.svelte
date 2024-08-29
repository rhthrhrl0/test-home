<script>
    import Header from "./Header.svelte";
    import Footer from "./Footer.svelte";
    import {getNews} from "../../assets/news.js";

    // params 가져오기
    export let params = {}; // 객체로 받아옴
    console.log(params);
    console.log(params.id);
    let id = Number(params.id);
    let news = getNews(id);
</script>

<Header/>
<main class="container">
    <div class="main-header">
        <h2>{news.title}</h2>
        <p class="date">{news.date}</p>
        <img src={news.detailImgUrl} alt="">
    </div>
    <article>
        {@html news.desc}
    </article>
</main>
<Footer/>

<style lang="scss">
  .main-header {
    h2 {
      margin-bottom: 10px;
    }

    .date {
      margin-bottom: 20px;
      font-size: 15px;
      color: #666;
    }

    img {
      object-position: center;
      object-fit: cover;
      width: 100%;
    }
  }

  article {
    margin-top: 50px;
  }

  .container {
    background: #fff;
  }

  .item-text {
    padding: 20px;
  }
</style>
<script>
    import Header from "./Header.svelte";
    import Footer from "./Footer.svelte";

    import news from "../../assets/news.js";

    console.log(news);

</script>

<Header/>
<main class="container">
    <div class="news">
        {#each news as item}
            <a href="#/detail/{item.id}" class="news-item" style="width: calc(100% / {news.length})">
                <img src={item.imgUrl} alt="">
                <div class="item-text">
                    <h3>{item.title}</h3>
                    <p class="date">{item.date}</p>

                    <div class="hashtag">
                        {#each item.hashtag as tag}
                            <span>#{tag}</span>
                        {/each}
                    </div>
                </div>
            </a>
        {/each}
    </div>
</main>
<Footer/>

<style lang="scss">
  .news {
    display: flex;
    gap: 20px;

    .news-item {
      display: inline-block;

      // 그림자 효과
      box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.2);

      img {
        width: 100%;
        object-fit: cover;
        object-position: center;
      }
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    h3 {
      margin-bottom: 10px;
    }

    p {
      margin-bottom: 4px;
    }

    .date, .hashtag {
      font-size: 15px;
      color: #666;
    }
  }

  .container {
    background: #fff;
  }

  .item-text {
    padding: 20px;
  }
</style>
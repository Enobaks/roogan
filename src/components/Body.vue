<template>
  <div class="body-wrap">
    <div class="hero-section">
      <div class="hero-content">
        <div class="prefix">
          <hr />
          <small>the ultimate</small>
        </div>
        <h1>Podcasting Experience</h1>
        <p>
          Roogan is a fully-featured audio streaming website to help you set up
          and manage your audio podcast in no time. Let your voice be heard!
        </p>
        <div class="listen">
          <button><i class="fa fa-play" aria-hidden="true"></i></button>
          <span>start listening</span>
        </div>
      </div>
    </div>
    <!-- audio section -->
    <div class="audio-wrap">
      
      <div class="podcast" v-for="podcast in podcastList" :key="podcast.id">
        <!-- <div class="podcast-img">{{ podcast.logo }}</div> -->
        <img :src="podcast.logo" alt="" class="podcast-img">
        <div class="listen">
          <img src="../assets/images/headphone.png">
        </div>
        <div class="podcast-txt">
          <h2>Title</h2>
          <p>{{ podcast.name }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Body",
  data() {
    return {
      podcastList: [],
    };
  },
  mounted() {
    axios
      .get(`https://jollofradio.com/api/podcasts`)
      .then((res) => {
        this.podcastList = res.data.data; console.log(res);
        console.log(res.data);
        console.log(res.data.data[100]);
      })
      .catch((e) => {
        console.log(e);
        // this.errors.push(e)
      });
  },
};
</script>

<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.body-wrap {
  width: 100%;
  height: 92vh;
  color: #fff;

  .hero-section {
    width: 100%;
    height: 100%;
    background: url(../assets/images/roogan_hero.jpg);
    background-repeat: no-repeat;
    background-position: center;
    display: flex;
    align-items: center;
    position: relative;

    .hero-content {
      width: 50%;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      position: absolute;
      left: 8.8rem;
      // background: rgba(122, 120, 118, 0.274);

      .prefix {
        display: flex;
        align-items: center;
        text-transform: uppercase;

        hr {
          width: 1rem;
          margin-right: 5px;
        }
      }
      h1 {
        margin: 0.5rem 0 1rem;
        font-size: 2.6rem;
        text-align: left;
        letter-spacing: 0.5px;
        font-weight: 700;
      }
      p {
        text-align: left;
        width: 60%;
        line-height: 1.5rem;
        font-weight: 500;
      }
      .listen {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        margin: 1.5rem 0;

        button {
          height: 3.5rem;
          width: 3.5rem;
          border: none;
          border-radius: 30px;
          background-color: #67dbdb;
          color: #fff;
          font-weight: 550;
          text-align: center;
          margin-right: 10px;

          i {
            font-size: 1rem;
            font-weight: 600;
          }
        }
        span {
          font-weight: 600;
        }
      }
    }
  }
  .audio-wrap {
    width: 100%;
    height: 70rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-top: 2rem;
    padding: 5rem;

    .podcast {
      width: 26%;
      height: auto;
      border: 1px solid rgb(211, 209, 209);
      margin-bottom: 5rem;
      border-radius: 10px;
      position: relative;

      .podcast-img{
          width: 100%;
          height: 20rem;
          object-fit: cover;
          border-radius: 10px 10px 0 0;
      }

      .listen{
        width: 50px;
        height: 50px;
        background: rgba(187, 187, 187, 0.205);
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 10px;
        position: absolute;
        top: 5px;
        right: 5px;
       
        img{
          width: 25px;
          height: 25px;
        }
      }
      .podcast-txt{
          color: #000;
          margin-top: 1rem;
          display: flex;
          flex-direction: column;
          align-items: center;
          justify-content: center;
          height: 6rem;

          h2,p{
            margin-bottom: .5rem;
          }

      }
    }
  }
}
</style>
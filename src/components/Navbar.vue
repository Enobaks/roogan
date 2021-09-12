<template>
  <div class="nav-wrap">
    <nav>
      <div class="nav-content">
        <div class="test-nav">
          <div class="nav-responsive">
            <router-link class="nav-brand" to="/">
              <img :src="image" alt="">
            </router-link>
          </div>
          <div class="nav-link-container" v-show="!mobile">
            <!-- <form class="form-wrap">
              <input class="" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success" type="submit">Search</button>
            </form> -->
            <ul>
              <li>
                <router-link class="navbar-link active" to="/">Home</router-link>
              </li>
              <li>
                <router-link class="navbar-link" to="/">Cart</router-link>
              </li>
              <li>
                <router-link class="navbar-link" to="/">Help</router-link>
              </li>
              <li>
                <button class="login-btn" @click="openLoginForm">Login</button>
              </li>
            </ul>
          </div>
        </div>
        <button class="bars" v-show="mobile">
          <span><i class="fa fa-bars" aria-hidden="true" @click="toggleMobileNav" v-show="mobile" :class="{'icon-active': mobileNav}"></i></span>
        </button>
        <transition name="mobile-nav">
          <div class="nav-link-mobile" v-show="mobileNav">
            <form class="form-wrap">
              <input class="" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success" type="submit">Search</button>
            </form>
            <ul>
              <li>
                <router-link class="navbar-link active" to="/">Home</router-link>
              </li>
              <li>
                <router-link class="navbar-link" to="/">Cart</router-link>
              </li>
              <li>
                <router-link class="navbar-link" to="/">Help</router-link>
              </li>
              <li>
               <button class="login-btn" @click="openLoginForm">Login</button>
              </li>
            </ul>
          </div>
        </transition>
      </div>
    </nav>
  </div>  
</template>

<script>
import brand from '../assets/images/roogan_logo.png'
export default {
  name: 'Navbar',
  data () {
    return {
      mobile: true,
      mobileNav: null,
      windowWidth: null,
      image: brand
    }
    
  },
  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
  },
  methods: {
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav
    },

    checkScreen() {
      this.windowWidth = window.innerWidth;
      if (this.windowWidth <= 1000) {
        this.mobile = true;
        return;
      }
      this.mobile = false;
      this.mobileNav = false
    },
    openLoginForm() {
      this.$emit('open')
    }
  } 
}
</script>

<style scoped>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.test-nav{
  display: flex;
  justify-content: space-between;
}
.nav-wrap{
  background: #000;
  color: #fff;
  /* height: 10vh */
  
}
.nav-content{
  display: flex;
  flex-direction: column;
  width: 80%;
  justify-content: space-between;
  margin: auto;
  padding: .5rem;
  position: relative;
}

.nav-brand{
  text-decoration: none;
  font-size: 2rem;
  font-weight: 700;
  color: #232127;
}
.nav-responsive{
  width: fit-content;
}
.nav-link-container{
  width: 50%;
  display: flex;
  justify-content: flex-end;
}
.nav-link-container ul{
  list-style: none;
  margin: 0;
  padding: 0;
  width: 70%;
  display: flex;
  justify-content: space-between;
}
.nav-link-container ul li{
  float: left
}
.nav-link-container li a {
  display: block;
  padding: 8px;
  text-decoration: none;
  font-weight: 600;
  color: #fff;
}
.form-wrap{
  display: flex;
  align-items: center;
}
.form-wrap input{
  width: 70%;
  margin-right: 7px;
  height: 5vh;
  border-radius: 8px;
  border: 1px solid rgba(100, 99, 99, 0.575);
  padding: .5rem 1.5rem;
  outline: none;
}
@media (max-width: 1000px) {
  .form-wrap input, .form-wrap button{
    height: 2.5rem !important;
  }
  
}
.form-wrap button, .login-btn{
  height: 5vh;
  width: 4.5rem;
  border: none;
  border-radius: 5px;
  background-color: #67dbdb;
  color: #fff;
  font-weight: 550;
  text-align: center;
}

.bars span i{
  font-size: 2rem;
  color: #121213d7;
  transition: .8s ease all;
  cursor: pointer;
}
.bars span i.icon-active{
  transform: rotate(180deg);
}
.nav-responsive{
  justify-content: space-between;
  display: flex;
}
.bars{
  display: inline-block;
  width: 5%;
  outline: none !important;
  border: none !important;
  background: transparent !important;
  position: absolute;
  top: .5rem;
  right: 25px;
}
.bars span i{
  font-size: 2rem;
  color: #121213d7;
}
.nav-link-mobile{
  width: 100%;
  flex-direction: column;
  margin-top: 1rem;
}
.nav-link-mobile ul{
  display: flex;
  flex-direction: column;
  justify-content: start;
  list-style: none !important;
  margin-top: .5rem
}
.nav-link-mobile ul li{
  margin-top: 10px;
}
.nav-link-mobile ul a{
  text-decoration: none;
}
.nav-link-mobile{
  text-align: left;
}
.off{
  display: none;
}
.mobile-nav-enter-active, .mobile-nav-leave-active {
  transition: opacity .5s;
}
.mobile-nav-enter-from, .mobile-nav-leave-to{
  opacity: 0;
}

</style>
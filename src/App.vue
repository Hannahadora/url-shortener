<template>
<div id="app">
    <Header />
    <div class="bo1 lg:px-24 md:px-12 px-5 py-10 md:mt-10 flex md:flex-row flex-col items-center justify-between">
      <div class="overflow-x-hidden md:absolute right-0 top-32">
        <img class="relative -right-24 " alt="illust" src="./assets/images/illustration-working.svg" />
      </div>

      <div class="md:w-1/2 w-full mt-10 md:text-left text-center">
        <h1 class="font-bold md:text-7xl text-5xl">More than just shorter links</h1>
        <p class="my-7 text-2xl">Build your brand's recognition and get detailed insights on how your links are performing.</p>
        <Button text="Get Started" theme="primary"/>
      </div>
    </div>
    

    <div class="bo2 w-full bg-gray-100 lg:px-24 md:px-12 px-5 pb-24 mt-48">
      <form @submit.prevent="shortenLink" class="w-full rounded-xl relative -top-16 p-7">
          <div class="flex md:flex-row flex-col items-center justify-center gap-5">
            <input type="text" v-model="urlLinks" class="box bg-white focus:outline-none md:w-10/12 w-full p-4 border rounded-lg text-base" placeholder="Shorten a link here...">
            <input type="submit" value="Shorten It!" class="md:w-auto w-full cursor-pointer text-white rounded-lg px-7 py-4" style="background-color: hsl(180, 66%, 49%);" />
          </div>
          <div v-if="errorMsg" id="errorMsg">{{ errorMsg }}</div>
      </form>

      <div v-if="loading" class="loader w-2/12 mx-auto">
        <img class="mx-auto" src="./assets/images/loader.gif" alt="">
      </div>

     <div v-if="shortLinks" class="linkDisplay text-xl flex md:flex-row flex-col md:items-center items-start justify-between bg-white p-5">
        <a class="w-full md:border-0 border-b-2 p-1" href="">{{ original_link }}</a>
        <div class="md:w-1/2 w-full flex md:flex-row flex-col items-start gap-5">
          <a href="" class="md:w-10/12 w-full p-1" style="color: hsl(180, 66%, 49%);">{{ full_short_link }}</a>
          <!-- <Button class="w-full" text="Copy" @click.prevent="copyLink"/> -->
          <div @click.prevent="copyLink">
            <p v-if="!copy" class="w-full cursor-pointer py-2 px-4 rounded text-white" style="background-color: hsl(180, 66%, 49%);">Copy</p>
            <p v-if="copy" class="w-full cursor-pointer bg-black py-2 px-4 rounded text-white">Copied</p>
          </div>
        </div>
     </div>

      <div class="md:w-5/12 w-full mx-auto my-10 text-center">
        <h1 class="text-black font-bond text-2xl">Advanced Statistics</h1>
        <p class="mt-5 text-lg">Track how your links are performing across the web with our advanced statistics dashboard.</p>
      </div>

      <div class="w-full md:mt-4 mt-40 flex md:flex-row flex-col items-center justify-between">
        <div class="textbox px-10 pb-10 flex flex-col md:items-start items-center bg-white rounded">
          <img src="./assets/images/icon-brand-recognition.svg" alt="" class="imgIcon relative -top-10" />
          <h1>Brand Recognition</h1>
          <p class="md:text-left text-center">Boost your brand recognition with each click. Generic links don’t mean a thing. Branded links help instil confidence in your content.</p>
        </div>
        <div class="border md:h-2 h-12 md:w-12 w-2" style="background-color: hsl(180, 66%, 49%);"></div>
        <div class="textbox px-10 pb-10 flex flex-col md:items-start items-center bg-white rounded md:mt-20 mt-7">
          <img src="./assets/images/icon-detailed-records.svg" alt="" class="imgIcon relative -top-10" />
          <h1>Detailed Records</h1>
          <p class="md:text-left text-center">Gain insights into who is cliking your links. Knowing when and where people engage with your content helps inform better decisions.</p>
        </div>
        <div class="border md:h-2 h-12 md:w-12 w-2" style="background-color: hsl(180, 66%, 49%);"></div>
        <div class="textbox px-10 flex flex-col md:items-start items-center pb-10 bg-white rounded md:mt-40 mt-7">
          <img src="./assets/images/icon-fully-customizable.svg" alt="" class="imgIcon relative -top-10" />
          <h1>Fully Customizable</h1>
          <p class="md:text-left text-center">Improve brand awareness and content discoverability through customizable link, supercharging audience engagement.</p>
        </div>
      </div>
    </div>

    <div class="bo3 w-full py-20 text-center text-white bg-no-repeat">
      <h1 class="mb-5 font-bold text-3xl">Boost your links today</h1>
      <Button text="Get Started" theme="primary"/>
    </div>

    <Footer />
  </div>
</template>








<script>
import Header from './components/Header.vue'
import Button from './components/Button.vue'
import Footer from './components/Footer.vue'


export default {
  name: 'App',
  components: {
    Header,
    Button,
    Footer
  },

  data() {
    return {
      urlLinks: '',
      errorMsg: '',
      shortLinks: false,
      original_link: '',
      full_short_link: '',
      loading: false,
      copy: false
    }
  },

  methods: {
    shortenLink(e) {
        this.errorMsg = this.urlLinks.length > 1 ? '' : 'Please add a link',
        this.loading = this.urlLinks.length > 1 ? true : false,
        this.copy = false,
        this.shortLinks = false,

        fetch(`https://api.shrtco.de/v2/shorten?url=${this.urlLinks}`) 
          .then((res) => res.json())
          .then((data) => {
            this.shortLinks = data.result
            this.original_link = this.shortLinks.original_link
            this.full_short_link = this.shortLinks.full_short_link
            // console.log(data)
          })

          .catch((err) => {
            this.errorMsg = 'Can\'t find Link'
          })

          .finally(() => {
             this.loading = false
          }) 
      },

    copyLink(e) {
      this.copy = true
      setTimeout(() => {
        this.copy = false
      }, 5000)
      const inputx = document.body.appendChild(document.createElement('input'));
      inputx.value = this.full_short_link;
      inputx.focus()
      inputx.select()
      document.execCommand("copy")
      inputx.parentNode.removeChild(inputx)
      console.log(inputx)

    }
      

      
  }
}
</script>










<style>
  #app {
    font-family: 'Poppins', sans-serif;
  }

  form {
    background-image: url('./assets/images/bg-shorten-desktop.svg');
    background-color: hsl(257, 27%, 26%);
  }

  .bo3 {
    background-image: url('./assets/images/bg-boost-desktop.svg');
    background-color: hsl(257, 27%, 26%);
  }

  p {
    color: hsl(257, 7%, 63%);
  }

  .imgIcon {
    background-color: hsl(255, 11%, 22%);
    border-radius: 50%;
    padding: 20px;
  }

  #errorMsg {
    color: hsl(0, 87%, 67%);
  }

  /* .loader {
    width: 30%;
    margin: 0 auto;
  } */
  
  /* .flex {
    display: flex;
    flex-direction: row;
    align-items: start;
  }

  @media (max-width: 540px) {
    .flex {
      flex-direction: column;
      align-items: center;
    }
  } */
</style>

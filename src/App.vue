<template>
  <div id="app">
    <div>
      <img v-bind:style="imageStyle" src="./assets/website_background.png">
      <h1 v-bind:style="messageStyle">Matthew O'Boyle</h1>
      <h1 v-bind:style="lowerStyle">Software Engineer</h1>
      <a href="mailto:mo121@cs.duke.edu?subject=Message from Website&body=Dear Matthew O'Boyle,"
         v-bind:style="lower2Style">Email me</a>
      <a href="resume.pdf" download="Matthew O'Boyle Resume.pdf" v-bind:style="lower3Style">Download Resume</a>
    </div>
    <div v-bind:style="thin">
      <h1>About</h1>
      <p>Hi there! My name's Matthew O'Boyle and I'm a Junior at Duke University interested in pursuing a career
        in Software Development. I love identifying and solving real-world problems through technology.
        Please get in touch if you have any questions!
      </p>
    </div>
    <div class="grey">
      <h1 v-bind:style="center">Experience</h1>
      <div v-for="thing in experience">
        <Experience
          v-bind:date=thing.date
          v-bind:info=thing.info
          v-bind:title=thing.title
          v-bind:position=thing.position />
      </div>
    </div>
    <div>
      <h1 v-bind:style="center">Portfolio</h1>
      <div class="row" >
        <Project v-for="proj in projects"
                 class="col-12 col-lg-6"
                 v-bind:info="proj.info"
                 v-bind:name="proj.name"
                 v-bind:demo="proj.demo"
                 v-bind:image="proj.image"
        />
      </div>
    </div>
    <div class="row grey">
      <div v-bind:style="{textAlign: 'center'}" class="col-md-4">
        <!--<h1 v-bind:style="{textAlign: 'center'}">Duke University</h1>-->
        <h3 v-bind:style="{marginBottom: '2vh'}">Relevant coursework</h3>
        <ul>
          <li>Computer Architecture (C)</li>
          <li>Data Structures and Algorithms </li>
          <li>Databases (SQL)</li>
          <li>Delivering Software (React-Native)</li>
          <li>Design & Analysis of Algorithms (Java)</li>
          <li>Discrete Mathematics for Computer Science (Scheme)</li>
          <li>Introduction to Computer Science (Python)</li>
          <li>Linear Algebra and Applications </li>
          <li>Probability and Statistical Inference</li>
          <li>Software Design/Implementation (Java)</li>
          <li>Web Application Development (Vue)</li>
        </ul>

      </div>
      <div class="col-md-7">
        <h3 v-bind:style="{textAlign: 'center'}">Skills</h3>
        <line-chart/>
      </div>

    </div>
    <div>


    </div>
    <div v-bind:style="thin">
      <h1>Outside the Classroom</h1>
      <h5>Camp Kesem</h5>
      <p>For the past 2 years, I have been head of Operations Committee at Camp Kesem -- a camp that supports children
        through and beyond a parent's cancer. This involves planning and fundraising throughout the year and culminates
        at a week-long summer camp completely free for the campers to attend.
      </p>
      <h5>Tennis</h5>
      <p>From the age of 7, I have played tennis at a competitive level. Throughout high school, I represented my country
        on numerous occasions in junior events, finishing 4th in Ireland before moving to college.
        I also coached many other top junior players in my club.
        I currently play on Duke's club tennis team.
      </p>
      <h5>Music</h5>
      <p>I achieved ABRSM Grade 8 piano and clarinet and taught myself saxophone in high school. For the past two semesters, I
        have played piano for patients and family members at Duke Hospital.
      </p>
    </div>
    <div class="grey">
      <h1 class="col-xs-12" v-bind:style="thin">View More</h1>
      <div v-bind:style="flex">

        <a href="https://github.com/oboyle-matthew" target="_blank" title="View my Github">
          <img  class="image" src="./images/github.png"/>
        </a>
        <a href="https://www.linkedin.com/in/matthewoboyle1/" target="_blank" title="View my LinkedIn">
          <img id="linked" class="image" src="./images/linkedin.png"/>
        </a>

      </div>
      <div v-bind:style="flex">
        <a href="resume.pdf" download="Matthew O'Boyle Resume.pdf" title="Download my Resume">
          <img class="image resume" src="./images/resume.png"/>
          <p v-bind:style="{textAlign: 'center'}">Download my Resume</p>
        </a>
        <a href="mailto:mo121@cs.duke.edu?subject=Message from Website&body=Dear Matthew O'Boyle," title="Send me an email">
          <img id="mail" class="image" src="./images/email.png"/>
        </a>
      </div>
    </div>

  </div>
</template>



<script>

  import Experience from "./components/Experience";
  import Project from "./components/Project";
  import Vue from 'vue';
  import VueChartJs from 'vue-chartjs';
  import experience from './experience.json';
  import projects from './projects.json';

  Vue.component('line-chart', {
    extends: VueChartJs.Bar,
    mounted () {
      this.renderChart({
        labels: ['Java', 'React', 'React-Native', 'Vue', 'Python', 'C', 'Scheme', 'MIPS'],
        datasets: [
          {
            label: 'Proficiency',
            backgroundColor: '#f87979',
            data: [10, 10, 8, 7, 4, 3, 2, 2, 0]
          }
        ],
        tooltips: false
      }, {tooltips: {enabled: false}, responsive: true, maintainAspectRatio: false})
    }
  });

  export default {
  name: 'app',
  data () {
    return {
      experience: experience,
      projects: projects,
      msg: 'Welcome to Your Vue.js App',
      flex: {
        display: 'flex',
        flexDirection: 'row',
        marginLeft: '35vw',
        marginRight: '35vw',
        marginTop: '5vh'
      },
      divStyle: {
        display: 'inline-block'
      },
      pStyle: {
        backgroundColor: 'yellow',
        width: '50vw'
      },
      half: {
        position: 'relative',
        // backgroundColor: 'green',
        marginLeft: '5vw',
        marginRight: '5vw',
        marginTop: '2vh',
        marginBottom: '2vh',
        width: '40vw'
      },
      imageStyle: {
        width: '100vw',
        height: '100vh',
        overflow: 'none'
      },
      messageStyle: {
        fontWeight: 'bolder',
        fontSize: '4vw',
        position: 'absolute',
        color: 'white',
        top: '20vh',
        width: '100vw',
        textAlign: 'center',
        overflow: 'none'
      },
      lowerStyle: {
        fontWeight: 'bolder',
        fontSize: '2.5vw',
        position: 'absolute',
        color: 'white',
        top: '30vh',
        width: '100vw',
        textAlign: 'center',
        overflow: 'none'
      },
      lower2Style: {
        fontWeight: 'bolder',
        fontSize: '3vw',
        position: 'absolute',
        color: 'white',
        left: '37vw',
        top: '55vh',
        overflow: 'none'
      },
      lower3Style: {
        fontWeight: 'bolder',
        fontSize: '2.8vw',
        position: 'absolute',
        color: 'white',
        left: '52vw',
        top: '54.5vh',
        width: '13vw',
        overflow: 'none',
        wordSpacing: '100vw',
        lineHeight: '5vh',
        textAlign: 'center'
      },
      thin: {
        position: 'relative',
        left: '20vw',
        right: '20vw',
        width: '60vw',
        textAlign: 'center'
      },
      center: {
        textAlign: 'center'
      }
    }
  },
  components: {
    Experience,
    Project
  }
}
</script>

<style>
  * {
    margin: 0;
  }

  #app {
    overflow-x: hidden;
  }

  li {
    font-size: 1.2vw;
    margin-top: 1.3vh;
  }

  .image {
    width: 15vw
  }

  #linked {
    margin-top: -2vh;
    width: 20vw
  }

  #mail {
    margin-top: -4vh;
    width: 20vw;
  }

  .resume {
    height: 25vh;
  }

  * {
    font-family: 'sans-serif';
  }

  .grey {
    background-color: #f0f0f0;
  }
</style>

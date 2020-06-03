<template>
  <div class="resume" id="resume2">
    <div class="left-column">
      <div>
        <div class="headline">
          {{ person.name }}
        </div>
        <br/>
        <span class="txt-full-white"> {{ person.position }} </span>
        <br/>
        <span> {{ person.contact.city }} </span>
      </div>

      <div class="txt-full-white multi-line-txt">
        {{ person.about }}
      </div>

      <div class="social-container">
        <a :href="contactLinks.email" class="external-link">
          <i class="fa fa-envelope contact-icon"></i>
          <span class="block-marged txt-full-white">
            {{ person.contact.email }}
          </span>
        </a>

        <a v-if="person.contact.website"
          :href="contactLinks.website"
          class="external-link">

          <i class="fa fa-globe contact-icon"></i>
          <span class="block-marged txt-full-white">
            {{ person.contact.website }}
          </span>
        </a>

        <a v-if="person.contact.github"
          :href="contactLinks.github"
          class="external-link">

          <i class="fa fa-github contact-icon"></i>
          <span class="block-marged txt-full-white">
            {{ person.contact.github }}
          </span>
        </a>

        <a v-if="person.contact.linkedin"
          :href="contactLinks.linkedin"
          class="external-link">

          <i class="fa fa-linkedin contact-icon"></i>
          <span class="block-marged txt-full-white">
            {{ person.contact.linkedin}}
          </span>
        </a>

        <a v-if="person.contact.medium"
          :href="contactLinks.medium"
          class="external-link">
          <i class="fab fa-medium contact-icon"></i>
          <span class="block-marged txt-full-white">
            {{ person.contact.medium }}
          </span>
        </a>
      </div>

      <div class="skills-container">
        <div class="left-icon">
          <i class="fa fa-cogs"></i>
          <span class="left-section-headline">Skills</span>
        </div>

        <div v-for="(skill, index) in person.skills" :key="index" class="section-content__item">
          <span class="section-content__header"> {{ skill.name}} </span> 
          <ul class="skill-highlights" style="padding-inline-start: 20px;">
          <li v-for="(highlights, index) in skill.highlights" :key="index" class="skill-highlights">
            {{ highlights }}
          </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="left-column-bg">
    </div>

    <div class="right-column">
      <div class="experience-section section">
        <div class="icon">
          <i class="material-icons small-icon">work</i>
          <span class="section-headline">{{ lang.experience }}</span>
        </div>

        <div class="section-content">
          <div v-for="(experience, index) in person.experience" :key="index"
            class="section-content__item">

            <span class="section-content__header"> {{ experience.position }} </span> 
            <span>&#8226;</span>
            <span class="section-content__subheader"> {{ experience.company }} </span>
            <div class="section-content__text--right"> {{ experience.timeperiod }}</div>
            <ul>
              <li v-for="(description, index) in experience.description" :key="index" class="section-content__text--light"> 
                {{ description }}
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="education-section section">
        <div class="icon">
          <i class="material-icons">school</i>
          <span class="section-headline">{{ lang.education }}</span>
        </div>

        <div class="section-content">
          <div v-for="(education, index) in person.education" :key="index"
            class="section-content__item">
            
            <span class="section-content__header"> {{ education.institution }} </span>
            <span class="section-content__text--right"> {{ education.timeperiod }} </span>
            <br>
            <span class="section-content__subheader">{{ education.degree }}</span>
            <ul>
              <li v-if="education.thesis" class="section-content__text--light">
                View Thesis <a :href="education.thesis" class="link">Here</a>
              </li>
              <li v-if="education.publications" class="section-content__text--light">
                View Publications <a :href="education.publications" class="link">Here</a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div v-if="person.projects"
        class="projects-section section">
        <div class="icon">
          <i class="material-icons">code</i>
          <span class="section-headline"> {{ lang.projects }} </span>
        </div>

        <div class="section-content">
          <div v-for="(project, index) in person.projects" :key="index"
            class="section-content__item"
            :href="project.url">

            <span class="section-content__header"> {{ project.name }} </span>
            <span class="section-content__subheader">{{ project.platform }}</span>
            <span class="section-content__text--right"> {{ project.description }} </span>
            <span class="section-content__text--light"> {{ project.url }} </span>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'eric-jalbert';

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>

@accent-color: #666699;

.resume {
  display: flex;
  position: relative;

  font-family:'Roboto' !important;
  font-size: 0.9em;
}

.left-column {
  width: 25%;
  height: 100%;
  padding: 30px;
  padding-top: 25px;
  text-align: left;

  color: #ffffff;
  color:rgba(255,255,255,1);
  background-color: @accent-color;
  overflow: hidden;
  display: block;
  z-index: 2;

  opacity: 1; // lower this value (0.7 approx.) to see the cover image
  position: absolute;
}

// Background cover displayed on the left-column side
// ------------
.left-column-bg {
  // You can put your own cover image in the url path
  // --------------------------------------
  // background: url('../assets/cover.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 25% 25%;
  opacity: .4; // up this value to contrast the cover image

  height: 100%;
  width: 30%;
  padding: 30px;
  padding-top: 25px;

  display: block;
  overflow: hidden;
  position: relative;
  top: 0;
  z-index: 1;
}

.right-column {
  display: flex;
  flex-direction: column;
  padding: 30px;

  height: 100%;
  width: 70%;
}

a {
  cursor:pointer;
  text-decoration-line: none;
}

.material-icons {
  color: @accent-color;
  position: relative;
  top: 5px;
}

.font-awesome-icons {
  color: @accent-color;
  font-size: 1.3em;
  margin-right: 6px;
}

.small-icon {
  top: 2.5px;
  font-size: 1.4em;
}

.contact-icon {
  color: white;
  font-size: 1.5em;
  margin-right: 10px;

  top: 2px;
  position: relative;
}

.contact-icon-svg {
  margin-top: -2.5px;
  margin-right: 10px;

  transform: scale(1);

  top: 5px;
  position: relative;
}

.contact-icon-svg path {
  fill: white;
}

.external-link {
  display: block;
  margin-bottom: 5px;
}

.block-marged {
  margin-top: 15px;
  margin-bottom: 15px;
}

.multi-line-txt {
  margin-top: 10px;
  margin-bottom: 20px;
}

.social-container {
  margin-top: 20px;
  margin-bottom: 20px;
}

.skills-container {
  .social-container
}

.headline {
  color: white;
  font-size: 2.5em;
  font-weight: bold;
}

.txt-full-white {
  color: white;
}

.uppercase {
  text-transform: uppercase;
}

.section-headline {
  color: @accent-color;
  display: inline-block;
  font-size: 1.2em;
  margin-left: 5px;
}

.section-content {
  margin-top: 10px;
  padding-left: 24px;
}

.section-content__item {
  display: block;
  margin-bottom: 10px;
}

.section-content__item-grid {
  flex: 1 1 0;

  margin-bottom: 10px;
  padding-right: 10px;
}

.section-content-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

  margin-top: 10px;
  margin-bottom: 10px;
  padding-left: 24px;
}

.grid-item {
  padding-right: 20px;
}

.section-content__header {
  display: inline-block;

  font-size: 1.1em;
  font-weight: 500;
}

.squarred-grid-item {
  display: block;

  border: 1px solid @accent-color;

  background-color: @accent-color;
  color: white;

  margin-top: 5px;
  padding: 5px;

  transition: .5s;

  &:hover {
    background-color: transparent;
    color: @accent-color;
    transition: .5s;
  }
}

.section-content__subheader {
  display: inline-block;
  font-weight: 400;
}

.section-content__text--right {
  display: block;
  float: right;
  font-weight: 300;
}

.section-content__text--light {
  color: rgba(0,0,0,0.95);
  font-weight: 300;
}

.section-content__subheader,
.section-content__text--light,
.section-content__header {
  line-height: 1.5em;
}

.section {
  margin-top: 10px;
  margin-bottom: 10px;
}

.left-icon {
  .material-icons;
  color: white;
}

.left-section-headline {
  .section-headline;
  color: white;
  margin-bottom: 10px;
}

.skills-highlights {
  padding-inline-start: 20px;
  color: white;
}

.subheadline {
  color: rgba(255, 255, 255, 1);
  font-size: 1.2em;

  display: block;
  margin-bottom: 10px;
}

</style>

<template>
  <div class="main-wrapper">
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary fixed-top" id="sideNav">
      <a class="navbar-brand js-scroll-trigger" href="#about">
        <span class="d-block d-lg-none">James Krizan</span>
        <span class="d-none d-lg-block">
          <img class="img-fluid img-profile rounded-circle mx-auto mb-2" src="./assets/img/profile.jpg" alt="">
        </span>
      </a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#about">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#experience">Experience</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#education">Education</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#skills">Skills</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#volunteerOther">Volunteer</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#awards">Awards</a>
          </li>
        </ul>
      </div>
    </nav>

    <div class="container-fluid p-0">

      <section class="resume-section p-3 p-lg-5 d-flex d-column" id="about">
        <div class="my-auto">
          <h1 class="mb-0">{{ name }}
            <span class="text-primary">{{ surname }}</span>
          </h1>
          <div class="subheading mb-5">{{ address }}
           ·
            <a :href="'mailto:' + email">{{ email }}</a>
          </div>
          <p class="mb-5">{{ aboutMe }}</p>
          <ul class="list-inline list-social-icons mb-0">
            <li class="list-inline-item">
              <a :href="facebookLink" target="_blank">
                <span class="fa-stack fa-lg">
                  <i class="fa fa-circle fa-stack-2x"></i>
                  <i class="fa fa-facebook fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
            <li class="list-inline-item">
              <a :href="twitterLink" target="_blank">
                <span class="fa-stack fa-lg">
                  <i class="fa fa-circle fa-stack-2x"></i>
                  <i class="fa fa-twitter fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
            <li class="list-inline-item">
              <a :href="linkedInLink" target="_blank">
                <span class="fa-stack fa-lg">
                  <i class="fa fa-circle fa-stack-2x"></i>
                  <i class="fa fa-linkedin fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
            <li class="list-inline-item">
              <a :href="githubLink" target="_blank">
                <span class="fa-stack fa-lg">
                  <i class="fa fa-circle fa-stack-2x"></i>
                  <i class="fa fa-github fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
          </ul>
        </div>
      </section>

      <section class="resume-section p-3 p-lg-5 d-flex flex-column" id="experience">
        <div class="my-auto">
          <h2 class="mb-5">Experience</h2>

          <div class="resume-item flex-column mb-5" v-for="(job, index) in experience" :key="index">
            <div class="d-flex flex-column flex-md-row">
              <div class="resume-content mr-auto">
                <h3 class="mb-0">{{ job.position }}</h3>
                <div class="subheading mb-3">
                  <a :href="job.companyLink" target="_blank">{{ job.company }}</a>
                </div>
                <p>{{ job.description }}</p>
              </div>
              <div class="resume-date text-md-right">
                <span class="text-primary">{{ job.startDate }} - {{ job.endDate }}</span>
              </div>
            </div>
            <div class="d-flex resume-content mt-4 flex-row flex-wrap">
              <div class="col-6 col-lg-4 text-center mb-4" v-for="(relatedSite, index) in job.relatedSites" :key="index">
                <a :href="relatedSite.link" target="_blank">
                  <img class="img-thumbnail" :src="'/static/' + relatedSite.image" />
                  <br />
                  <span>{{ relatedSite.name }}</span>
                </a>
              </div>
            </div>
          </div>

        </div>

      </section>

      <section class="resume-section p-3 p-lg-5 d-flex flex-column" id="education">
        <div class="my-auto">
          <h2 class="mb-5">Education</h2>

          <div class="resume-item d-flex flex-column flex-md-row mb-5" v-for="(item, index) in education" :key="index">
            <div class="resume-content mr-auto mb-2">
              <h3 class="mb-0">{{ item.school }}</h3>
              <div class="subheading mb-3">{{ item.degree }}</div>
              <div>{{ item.area }}</div>
              <p>GPA: {{ item.gpa }}</p>
              <ul class="fa-ul mb-0">
                <li v-for="(award, index) in item.awards" :key="index"><i class="fa-li fa fa-trophy text-warning"></i>{{ award }}</li>
              </ul>
            </div>
            <div class="resume-date text-md-right">
              <span class="text-primary">{{ item.startDate }} - {{ item.endDate }}</span>
            </div>
          </div>

        </div>
      </section>

      <section class="resume-section p-3 p-lg-5 d-flex flex-column" id="skills">
        <div class="my-auto">
          <h2 class="mb-5">Skills</h2>

          <div class="subheading mb-3">Programming Languages &amp; Tools</div>
          <ul class="list-inline list-icons">
            <li class="list-inline-item" v-for="(skill, index) in skills" :key="index"><a href="" target="_blank"><i :class="'devicons devicons-' + skill"></i></a></li>
          </ul>

          <div class="subheading mb-3">Workflow</div>
          <ul class="fa-ul mb-0">
            <li>
              <i class="fa-li fa fa-check"></i>
              Mobile-First, Responsive Design</li>
            <li>
              <i class="fa-li fa fa-check"></i>
              Cross Browser Testing &amp; Debugging</li>
            <li>
              <i class="fa-li fa fa-check"></i>
              Cross Functional Teams</li>
            <li>
              <i class="fa-li fa fa-check"></i>
              Agile Development &amp; Scrum</li>
          </ul>
        </div>
      </section>

      <section class="resume-section p-3 p-lg-5 d-flex flex-column" id="volunteerOther">
        <div class="my-auto">
          <h2 class="mb-5">Volunteer & Other Experience</h2>

          <div class="resume-item flex-column mb-5" v-for="(volunteerOther, index) in volunteer" :key="index">
            <div class="d-flex flex-column flex-md-row">
              <div class="resume-content mr-auto">
                <h3 class="mb-0"><a :href="volunteerOther.link" target="_blank">{{ volunteerOther.name }}</a> - {{ volunteerOther.location }}</h3>
                <div class="subheading mb-3">
                  <ul>
                    <li v-for="(role, index) in volunteerOther.roles" :key="index">{{ role }}</li>
                  </ul>
                </div>
                <p>{{ volunteerOther.description }}</p>
              </div>
            </div>
            <div class="d-flex resume-content mt-4 flex-row flex-wrap">
              <div class="col-6 col-lg-4 text-center mb-2" v-for="(relatedSite, index) in volunteerOther.relatedSites" :key="index">
                <a :href="relatedSite.link" target="_blank">
                  <img class="img-thumbnail" :src="'/static/' + relatedSite.image" />
                </a>
              </div>
            </div>
          </div>

        </div>
      </section>

      <section class="resume-section p-3 p-lg-5 d-flex flex-column" id="awards">
        <div class="my-auto">
          <h2 class="mb-5">Awards &amp; Certifications</h2>
          <div class="subheading mb-3">Awards & Honors</div>
          <ul class="fa-ul mb-0">
              <ul class="fa-ul mb-0">
                <li v-for="(award, index) in awards" :key="index"><i class="fa-li fa fa-trophy text-warning"></i>{{ award }}</li>
              </ul>
          </ul>
          <div class="subheading mb-3 mt-3">Presentations</div>
          <ul>
            <li>CELEA Conference 2016</li>
          </ul>
        </div>
      </section>

    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'James Krizan || Full-Stack Web Developer',
      name: 'James',
      surname: 'Krizan',
      address: 'New York, NY',
      email: 'jameskrizan@outlook.com',
      aboutMe: 'Experienced web developer specializing in full-stack JavaScript implementations.',
      facebookLink: 'https://www.facebook.com/jaskrizan',
      twitterLink: 'https://twitter.com/jameskrizan',
      linkedInLink: 'https://www.linkedin.com/in/jameskrizan',
      githubLink: 'https://github.com/jameskrizan',
      experience: [
        {
          position: 'Test Engineer',
          company: 'Real-Time Technology Solutions (RTTS)',
          companyLocation: 'New York, NY',
          companyLink: 'https://www.rttsweb.com',
          startDate: 'July 2017',
          endDate: 'Present',
          description: 'Managed the testing data and analytics for a $1.5 billion project, using industry-standard software.'
        },
        {
          position: 'Web Developer',
          company: 'James Krizan Web Development',
          companyLocation: 'New York, NY',
          companyLink: 'https://jameskrizan.com',
          startDate: 'January 2016',
          endDate: 'July 2017',
          description: 'Designed custom websites for clients using HTML5, JavaScript, and CSS, using popular content management systems including WordPress and Weebly.',
          relatedSites: [{name: 'Central Presbyterian Church', image: 'cpc.png', link: 'https://www.centralchurchnyc.org'}, {name: 'Margaret Kemmerer Artist Portfolio', image: 'kemmerer.png', link: 'https://margaretkemmerer.com'}, {name: 'Thrive International Programs', image: 'thrive.png', link: 'https://thriveip.org'}, {name: 'Gail Martensen Artist Portfolio', image: 'martensen.png', link: 'https://gailmartensenart.com'}, {name: 'Chef Co-op Programs', image: 'chef.png', link: 'https://http://chefco-op.com'}]
        },
        {
          position: 'Web Developer',
          company: 'Lycoming College',
          companyLocation: 'Williamsport, PA',
          companyLink: 'https://www.lycoming.edu',
          startDate: 'December 2012',
          endDate: 'January 2016',
          description: 'Provided online and in person support to various academic departments regarding their web pages.',
          relatedSites: [{name: 'Lycoming College', image: 'lycoming.png', link: 'https://www.lycoming.edu'}, {name: 'Underground Railroad Historical Site', image: 'ugrr.png', link: 'https://www.lycoming.edu/art/underground/'}]
        }
      ],
      education: [
        {
          school: 'Lycoming College',
          degree: 'Bachelor of Arts',
          area: 'Computer Science (Web Design and Development)',
          gpa: '3.92',
          startDate: 'September 2012',
          endDate: 'January 2016',
          awards: ['Summa Cum Laude', 'Dean\'s List', 'Phi Kappa Phi Honor Society', 'Iota Alpha Kappa Honor Society', 'Omicron Delta Kappa Honor Society', 'Kocian Award in Mathematics']
        },
        {
          school: 'University of Rochester',
          degree: 'Bachelor of Science',
          area: 'Computational Linguistics',
          gpa: '3.60',
          startDate: 'September 2011',
          endDate: 'May 2012',
          awards: ['Dean\'s List']
        }
      ],
      skills: ['html5', 'npm', 'wordpress', 'bootstrap', 'sass', 'jquery', 'css3', 'javascript_badge', 'angular', 'bitbucket', 'github_badge', 'jira', 'java', 'ruby', 'ruby_on_rails', 'modernizr', 'nodejs', 'less', 'bower', 'photoshop', 'docker', 'eclipse', 'dreamweaver'],
      volunteer: [
        {
          name: 'Together One New York (TONY)',
          location: 'Hell\'s Kitchen, NY',
          link: 'https://togetheronenewyork.org',
          roles: ['Director of Children\'s Programming', 'Director of the TASC Program', 'TASC, ESL, & Spanish Teacher', 'Board Member'],
          description: ''
        },
        {
          name: 'River Valley Internet',
          location: 'Montoursville, PA',
          link: 'http://www.rivervalleyinternet.net/',
          roles: ['Wireless Installation Technician'],
          description: ''
        },
        {
          name: 'West Branch School',
          location: 'Williamsport, PA',
          link: 'https://www.westbranchschool.org/',
          roles: ['Computer Science & Spanish Teacher'],
          description: ''
        },
        {
          name: 'Lycoming College Academic Resource Center',
          location: 'Williamsport, PA',
          link: 'https://www.lycoming.edu/academic-resource-center/',
          roles: ['Computer Science, ESL, and Spanish Tutor'],
          description: ''
        },
        {
          name: 'Thrive International Programs',
          location: 'Williamsport, PA',
          link: 'https://thriveip.org',
          roles: ['Co-Founder', 'Vice President', 'Web Developer', 'ESL & Spanish Teacher'],
          description: '',
          relatedSites: [{image: 'thrive.png', link: 'https://thriveip.org'}]
        },
        {
          name: 'Nativity Preparatory Academy',
          location: 'Rochester, NY',
          link: 'http://nativityrochester.org/',
          roles: ['Math Tutor'],
          description: ''
        }
      ],
      awards: ['Phi Kappa Phi Honor Society', 'Iota Alpha Kappa Honor Society', 'Omicron Delta Kappa Honor Society', 'Kocian Award in Mathematics']
    }
  },
  mounted () {
    const $ = this.jquery
    this.$nextTick(() => {
      // our custom jQuery code goes here
      $('a.js-scroll-trigger[href*="#"]:not([href="#"])').click(function () {
        if (location.pathname.replace(/^\//, '') === this.pathname.replace(/^\//, '') && location.hostname === this.hostname) {
          var target = $(this.hash)
          target = target.length ? target : $('[name=' + this.hash.slice(1) + ']')
          if (target.length) {
            $('html, body').animate({
              scrollTop: (target.offset().top)
            }, 1000, 'easeInOutExpo')
            return false
          }
        }
      })
      // Closes responsive menu when a scroll trigger link is clicked
      $('.js-scroll-trigger').click(function () {
        $('.navbar-collapse').collapse('hide')
      })
      // Activate scrollspy to add active class to navbar items on scroll
      $('body').scrollspy({
        target: '#sideNav'
      })
    })
  }
}
</script>

<style>
body {
  font-family: 'Open Sans', serif;
  padding-top: 54px;
  color: #868e96;
}
@media (min-width: 992px) {
  body {
    padding-top: 0;
    padding-left: 17rem;
  }
}
h1, h2, h3, h4, h5, h6 {
  font-family: 'Saira Extra Condensed', serif;
  font-weight: 700;
  text-transform: uppercase;
  color: #343a40;
}
h1 {
  font-size: 6rem;
  line-height: 5.5rem;
}
h2 {
  font-size: 3.5rem;
}
.subheading {
  text-transform: uppercase;
  font-weight: 500;
  font-family: 'Saira Extra Condensed', serif;
  font-size: 1.35rem;
}
.list-social-icons a {
  color: #495057;
}
.list-social-icons a:hover {
  color: #BD5D38;
}
.list-social-icons a .fa-lg {
  font-size: 1.75rem;
}
.list-icons {
  font-size: 3rem;
}
.list-icons .list-inline-item i:hover {
  color: #BD5D38;
}
#sideNav .navbar-nav .nav-item .nav-link {
  font-weight: 600;
  text-transform: uppercase;
}
@media (min-width: 992px) {
  #sideNav {
    text-align: center;
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    width: 17rem;
    height: 100vh;
  }
  #sideNav .navbar-brand {
    display: flex;
    margin: auto auto 0;
    padding: 0.5rem;
  }
  #sideNav .navbar-brand .img-profile {
    max-width: 10rem;
    max-height: 10rem;
    border: 0.5rem solid rgba(255, 255, 255, 0.2);
  }
  #sideNav .navbar-collapse {
    display: flex;
    align-items: flex-start;
    flex-grow: 0;
    width: 100%;
    margin-bottom: auto;
  }
  #sideNav .navbar-collapse .navbar-nav {
    flex-direction: column;
    width: 100%;
  }
  #sideNav .navbar-collapse .navbar-nav .nav-item {
    display: block;
  }
  #sideNav .navbar-collapse .navbar-nav .nav-item .nav-link {
    display: block;
  }
}
section.resume-section {
  border-bottom: 1px solid #dee2e6;
  padding-top: 5rem !important;
  padding-bottom: 5rem !important;
}
section.resume-section .resume-item .resume-date {
  min-width: none;
}
@media (min-width: 768px) {
  section.resume-section {
    min-height: 100vh;
  }
  section.resume-section .resume-item .resume-date {
    min-width: 18rem;
  }
}
@media (min-width: 992px) {
  section.resume-section {
    padding-top: 3rem !important;
    padding-bottom: 3rem !important;
  }
}
.bg-primary {
  background-color: #BD5D38 !important;
}
.text-primary {
  color: #BD5D38 !important;
}
a {
  color: #BD5D38;
}
a:hover, a:focus, a:active {
  color: #824027;
}
</style>

<template>
    <footer id="page-footer" class="footer">
      <div class="linksContainer">
        <div class="languageSwitch">
          <button class="button">
            <i class="fa-solid fa-globe"></i>
            <span>English</span>
          </button>
        </div>  
        <LinksList v-for="(group, idx) in links" :key="idx" :links="group" class="linksGroup" />
      </div>
  
      <div class="logoCopyRights">
        <NuxtLink to="/">
          <img
            src="../assets/logo-udemy.png" 
            alt="logo"
            class="logo"
          />
        </NuxtLink>
        <div class="copyRights">© 2024 Udemy, Inc.</div>
      </div>
    </footer>
  </template>
  
  <script setup>
  import LinksList from '~/components/common/LinksList.vue'; 
  
  const links = [
    [
        {
            text: 'Udemy Business',
            href: 'https://www.udemy.com/udemy-business/?locale=en_US&mx_pg=home-page&path=%2F&ref=footer'
        },
        {
            text: 'Teach on Udemy',
            href: 'https://www.udemy.com/teaching/?ref=teach_footer'
        },
        {
            text: 'Get the app',
            href: 'https://www.udemy.com/mobile/'
        },
        {
            text: 'About us',
            href: 'https://about.udemy.com/?locale=en-us'
        },
        {
            text: 'Contact us',
            href: 'https://about.udemy.com/company?locale=en-us#offices'
        }
    ],
    [
        {
            text: 'Careers',
            href: 'https://about.udemy.com/careers?locale=en-us'
        },
        {
            text: 'Blog',
            href: 'https://blog.udemy.com/?ref=footer'
        },
        {
            text: 'Help and Support',
            href: 'https://www.udemy.com/support/'
        },
        {
            text: 'Affiliate',
            href: 'https://www.udemy.com/affiliate/'
        },
        {
            text: 'Investors',
            href: 'https://investors.udemy.com/'
        }
    ],
    [
        {
            text: 'Terms',
            href: 'https://www.udemy.com/terms/'
        },
        {
            text: 'Privacy policy',
            href: 'https://www.udemy.com/terms/privacy/'
        },
        {
            text: 'Cookie settings',
            href: ''
        },
        {
            text: 'Sitemap',
            href: 'https://www.udemy.com/sitemap/'
        },
        {
            text: 'Accessibility statement',
            href: 'https://about.udemy.com/accessibility-statement?locale=en-us'
        }
    ]
];
  </script>
  
  <style scoped>
.footer {
    padding: 1rem;
}

.button {
    margin: 0;
    background-color: transparent;
    border: 1px solid #fff !important;
    padding: 0 1.6rem;
    height: 2.5rem;
    min-width: 9rem;
}

.footer,
.button {
    background-color: #1c1d1f;
    border-top: 1px solid #3e4143;
    color: white;
}

.button span {
    margin-left: 5px;
}

.button:hover {
    background-color: rgb(65, 70, 75);
}

.linksContainer {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.languageSwitch {
    padding: 1.5rem 0;
}

.logoCopyRights {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    flex-direction: column;
}

@media only screen and (min-width: 700px) {
    .linksContainer {
        flex-direction: row;
    }

    .languageSwitch {
        order: 1;
    }

    .languageSwitch {
        flex-grow: 1;
    }

    .logoCopyRights {
        flex-direction: row;
    }

    .copyRights {
        padding: 2rem 0;
    }
}
  </style>
  
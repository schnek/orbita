<template>
  <div class="wow2008">
    <div class="wow2008-topbar">
      <div class="wow2008-topbar__inner">
        <nav aria-label="External links">
          <a href="#">WorldofWarcraft.com</a>
          <span class="wow2008-topbar__divider"></span>
          <a href="#">The Armory</a>
          <span class="wow2008-topbar__divider"></span>
          <a href="#">Forums</a>
        </nav>
        <form class="wow2008-search" role="search" @submit.prevent>
          <label class="visually-hidden" for="wow-search">Search</label>
          <span class="wow2008-search__left"></span>
          <span class="wow2008-search__body">
            <input id="wow-search" type="search">
            <select aria-label="Search area">
              <option>Community Site</option>
              <option>Encyclopedia</option>
              <option>In-game Support</option>
              <option>Tech Support</option>
            </select>
            <button type="submit">Search</button>
          </span>
          <span class="wow2008-search__right"></span>
        </form>
      </div>
    </div>

    <div class="wow2008-stage">
      <header class="wow2008-header">
        <a class="wow2008-logo" href="/" aria-label="World of Warcraft home">
          <img src="/ascemu_tbc/images/templates/The_Burning_Crusade/wowlogo-front.gif" alt="World of Warcraft The Burning Crusade">
        </a>
      </header>

      <aside class="wow2008-left" aria-label="Main navigation">
        <div class="wow2008-ne-top-left" aria-hidden="true"></div>
        <div class="wow2008-ne-center" aria-hidden="true"></div>
        <div class="wow2008-ne-bottom-left" aria-hidden="true"></div>
        <div class="wow2008-ne-nav-bg" aria-hidden="true"></div>

        <nav class="wow2008-nav" aria-label="World of Warcraft sections">
          <section v-for="group in navigation" :key="group.key" class="wow2008-nav-section">
            <div
              class="wow2008-nav-button"
              :class="openGroups.includes(group.key) ? 'menu-button-on' : 'menu-button-off'"
              role="button"
              tabindex="0"
              :aria-expanded="openGroups.includes(group.key)"
              :aria-label="(openGroups.includes(group.key) ? 'Collapse ' : 'Expand ') + group.title"
              @click="toggleGroup(group.key)"
              @keydown.enter.prevent="toggleGroup(group.key)"
              @keydown.space.prevent="toggleGroup(group.key)"
            >
              <span
                class="wow2008-nav-icon"
                :class="{ 'is-wide': group.icon === 'interactive' || group.icon === 'support' }"
                :style="{ backgroundImage: 'url(' + menuAssets + 'icon-' + group.icon + '-' + (openGroups.includes(group.key) ? 'on' : 'off') + '.gif)' }"
                aria-hidden="true"
              ></span>
              <span
                class="wow2008-nav-title"
                :style="{ backgroundImage: 'url(' + menuAssets + 'header-' + group.header + '-' + (openGroups.includes(group.key) ? 'on' : 'off') + '.gif)' }"
                aria-hidden="true"
              ></span>
              <span
                class="wow2008-nav-collapse"
                :class="openGroups.includes(group.key) ? 'is-open' : 'is-closed'"
                aria-hidden="true"
              ></span>
              <span class="wow2008-nav-right-border" aria-hidden="true"></span>
            </div>

            <div v-if="openGroups.includes(group.key)" class="wow2008-nav-inner">
              <div class="leftMenu-cont-top"></div>
              <div class="leftMenu-cont-mid">
                <div class="m-left">
                  <div class="m-right">
                    <div class="leftMenu-cnt">
                      <ul class="mainNav">
                        <li v-for="link in group.links" :key="link">
                          <div class="wow2008-menu-entry">
                            <a href="#" class="menuFiller">{{ link }}</a>
                          </div>
                        </li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>
              <div class="leftMenu-cont-bot"></div>
            </div>
          </section>
        </nav>
      </aside>

      <main class="wow2008-center">
        <div class="wow2008-main-top">
          <div><div></div></div>
        </div>

        <div class="wow2008-main-content-wrapper">
          <div class="wow2008-main-content">
            <div class="wow2008-content-padding">
              <div class="wow2008-content-columns">
                <section class="wow2008-main-column">
                  <div class="wow2008-cnt-paper">
                    <div class="wow2008-cnt-top">
                      <div><div></div></div>
                    </div>
                    <div class="wow2008-content-left">
                      <div class="wow2008-content-right">
                        <div class="wow2008-cnt-main">
                          <div class="wow2008-news-column">
                            <div class="wow2008-flash-container">
                              <img class="wow2008-flash-placeholder" src="/ascemu_tbc/images/no-flash.jpg" alt="Welcome to World of Warcraft.com">
                            </div>
                            <div class="wow2008-news-heading">Latest News</div>
                            <slot>
                              <article class="wow2008-news-card">
                                <h1>Welcome to World of Warcraft</h1>
                                <p>Connect your Orbita news topics to publish announcements here.</p>
                              </article>
                            </slot>
                            <div class="wow2008-archive">
                              <a class="wow2008-archive-button" href="#" aria-label="View News Archives"></a>
                            </div>

                            <div class="wow2008-promo-grid">
                              <a class="wow2008-promo" href="#" aria-label="Contests">
                                <div class="wow2008-promo-frame">
                                  <span class="wow2008-promo-icon wow2008-promo-icon--contest"></span>
                                  <h3 class="wow2008-promo-title wow2008-promo-title--contest"><span>Contests</span></h3>
                                  <img src="/ascemu_tbc/images/featured/contest.jpg" alt="World of Warcraft screenshot contest">
                                  <span class="wow2008-read-more"></span>
                                </div>
                              </a>
                              <a class="wow2008-promo" href="#" aria-label="Fan Art">
                                <div class="wow2008-promo-frame">
                                  <span class="wow2008-promo-icon wow2008-promo-icon--fanart"></span>
                                  <h3 class="wow2008-promo-title wow2008-promo-title--fanart"><span>Fan Art</span></h3>
                                  <img src="/ascemu_tbc/images/featured/fanart.jpg" alt="World of Warcraft fan art">
                                  <span class="wow2008-read-more"></span>
                                </div>
                              </a>
                              <a class="wow2008-promo" href="#" aria-label="Wallpapers">
                                <div class="wow2008-promo-frame">
                                  <span class="wow2008-promo-icon wow2008-promo-icon--wallpaper"></span>
                                  <h3 class="wow2008-promo-title wow2008-promo-title--wallpaper"><span>Wallpapers</span></h3>
                                  <img src="/ascemu_tbc/images/featured/wallpaper.jpg" alt="World of Warcraft wallpaper">
                                  <span class="wow2008-read-more"></span>
                                </div>
                              </a>
                            </div>

                            <section id="container-community" class="wow2008-community">
                              <div class="phatLootBox-top wow2008-community-top">
                                <a href="/community/" class="wow2008-community-heading"><h2 class="community"><span class="visually-hidden">Community</span></h2></a>
                                <a href="/community/" class="wow2008-community-visual" aria-label="Community"></a>
                              </div>
                              <div class="phatLootBox-wrapper wow2008-community-wrapper">
                                <div class="community-top">
                                  <h3>Community Spotlight<i> - sch on 04/04/08 </i></h3>
                                </div>
                                <div class="community-cnt">
                                  <div class="community-portrait" aria-hidden="true"><img src="/ascemu_tbc/images/templates/The_Burning_Crusade/icon_communityspotlight.gif" alt=""></div>
                                  <p>
                                    This week we've come across some extremely beautiful and interesting artistic editing of in-game screenshots and characters.
                                    Wyndforge.com is home to an array of screenshots which he’s taken and dressed up with various filters, backdrops, and
                                    effects that turn a normal screenshot into something just a bit fancier. Check out Wyndforge's Art Gallery by
                                    <a href="http://wyndforge.com/" target="new_window" rel="noopener">clicking here</a>.
                                  </p>
                                  <div class="community-watch">
                                    Have you made or seen something that you think deserves to be on the World of Warcraft Community Watch? Send us a link at:
                                    <a href="mailto:">wowcommwatch</a>.
                                  </div>
                                  <p class="community-disclaimer"><small class="blood">
                                    * Links are created by other companies/individuals that are neither affiliated with nor supported by Blizzard Entertainment.
                                  </small></p>
                                  <div class="community-buttons">
                                    <ul>
                                      <li><div class="redButton-container">
                                        <span class="community-button-left"></span>
                                        <span class="community-button-label"><a href="/community/warcraftweekly.html">Warcraft Weekly</a><span class="rdbtn_sh">Warcraft Weekly</span></span>
                                        <span class="community-button-right"></span>
                                      </div></li>
                                      <li><div class="redButton-container">
                                        <span class="community-button-left"></span>
                                        <span class="community-button-label"><a href="/community/communitylinks.html">Spotlight Archive</a><span class="rdbtn_sh">Spotlight Archive</span></span>
                                        <span class="community-button-right"></span>
                                      </div></li>
                                    </ul>
                                  </div>
                                </div>
                              </div>
                              <div class="phatLootBox-bottom wow2008-community-bottom">
                                <a class="wow2008-community-read-more" href="/community/" aria-label="Read More"></a>
                              </div>
                            </section>

                            <div class="wow2008-banner-row">
                              <a class="wow2008-banner wow2008-banner--help" href="#" aria-label="Need Help">
                                <span class="wow2008-banner-icon wow2008-banner-icon--help"></span>
                                <span class="wow2008-banner-label wow2008-banner-label--help"></span>
                                <span class="wow2008-banner-read-more" aria-hidden="true"></span>
                              </a>
                              <a class="wow2008-banner wow2008-banner--jobs" href="#" aria-label="Jobs">
                                <span class="wow2008-banner-icon wow2008-banner-icon--jobs"></span>
                                <span class="wow2008-banner-label wow2008-banner-label--jobs"></span>
                                <span class="wow2008-banner-read-more" aria-hidden="true"></span>
                              </a>
                            </div>

                            <div class="wow2008-link-grid">
                              <section class="wow2008-link-group">
                                <h3><span>WoW: Wrath of the Lich King</span></h3>
                                <ul>
                                  <li><a href="#">Bestiary</a></li>
                                  <li><a href="#">Dragonblight</a></li>
                                  <li><a href="#">Screenshots</a></li>
                                  <li><a href="#">Features</a></li>
                                  <li><a href="#">Movies</a></li>
                                </ul>
                              </section>
                              <section class="wow2008-link-group">
                                <h3><span>Movies and Trailers</span></h3>
                                <ul>
                                  <li><a href="#">Sunwell Plateau</a></li>
                                  <li><a href="#">Verne Troyer</a></li>
                                  <li><a href="#">M.P.T.</a></li>
                                  <li><a href="#">William Shatner</a></li>
                                </ul>
                              </section>
                              <section class="wow2008-link-group">
                                <h3><span>World of Warcraft Insider</span></h3>
                                <p>Your number one source of up-to-date, behind the scenes information about World of Warcraft!</p>
                                <ul>
                                  <li><a href="#">Latest issue</a></li>
                                  <li><a href="#">Subscribe now</a></li>
                                </ul>
                              </section>
                              <section class="wow2008-link-group">
                                <h3><span>Online Store</span></h3>
                                <ul>
                                  <li><a href="#">World of Warcraft Battle Chest</a></li>
                                  <li><a href="#">World of Warcraft 2008 Daily Calendar</a></li>
                                  <li><a href="#">Burning Crusade Strategy Guide</a></li>
                                  <li><a href="#">TCG: Onyxia Raid Deck</a></li>
                                </ul>
                              </section>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="wow2008-cnt-bot">
                      <div><div></div></div>
                    </div>
                  </div>
                </section>

                <aside class="wow2008-right">
                  <section class="wow2008-bc-upgrade">
                    <h2><img src="/ascemu_tbc/images/templates/The_Burning_Crusade/header-expansion.jpg" alt="The Burning Crusade"></h2>
                    <div class="wow2008-bc-upgrade__content">
                      <img src="/ascemu_tbc/images/image-retailbox.gif" alt="World of Warcraft The Burning Crusade">
                      <div>
                        <strong>Digital Upgrade</strong>
                        <span>Burning Crusade</span>
                        <a href="#">Download Now</a>
                      </div>
                    </div>
                  </section>

                  <section class="wow2008-quicklinks">
                    <div class="wow2008-marginal-top">
                      <span class="wow2008-marginal-icon wow2008-marginal-icon--quicklinks"></span>
                      <h2></h2>
                    </div>
                    <div class="wow2008-marginal-body">
                      <ul>
                        <li v-for="link in quickLinks" :key="link"><a href="#">{{ link }}</a></li>
                      </ul>
                    </div>
                    <div class="wow2008-marginal-bottom"></div>
                  </section>

                  <section class="wow2008-screenshot">
                    <div class="wow2008-marginal-top">
                      <span class="wow2008-marginal-icon wow2008-marginal-icon--ssotd"></span>
                      <h2></h2>
                    </div>
                    <div class="wow2008-marginal-body wow2008-screenshot-body">
                      <div class="wow2008-screenshot__image" role="img" aria-label="Screenshot of the day"></div>
                      <select aria-label="Screenshot gallery">
                        <option>Screenshot Galleries</option>
                      </select>
                    </div>
                    <div class="wow2008-marginal-bottom"></div>
                  </section>

                  <section class="wow2008-newcomers">
                    <div class="wow2008-marginal-top">
                      <span class="wow2008-marginal-icon wow2008-marginal-icon--newcomers"></span>
                      <h2>Newcomers Section</h2>
                    </div>
                    <div class="wow2008-newcomers-body">
                      <div class="wow2008-newcomers-entry">
                        <img src="/ascemu_tbc/images/bg-newcomers.jpg" alt="">
                        <strong>Looking to purchase World of Warcraft?</strong>
                        <span>Follow the links below to learn more.</span>
                      </div>
                      <div class="wow2008-newcomers-entry">
                        <img src="/ascemu_tbc/images/bg-discover.jpg" alt="">
                        <strong>Lost in Azeroth?</strong>
                        <span>Find your way with our Beginner's Guide.</span>
                      </div>
                      <a href="#" class="wow2008-newcomers-button">General FAQ</a>
                    </div>
                    <div class="wow2008-marginal-bottom"></div>
                  </section>
                </aside>
              </div>
            </div>
          </div>
        </div>

        <footer class="wow2008-main-bottom">
          <div><div>
            <div class="wow2008-blizz-logo">
              <img src="/ascemu_tbc/images/new/bot-blizzlogo.gif" alt="Blizzard Entertainment">
            </div>
          </div></div>
        </footer>
      </main>

      <img class="wow2008-statue-left" src="/ascemu_tbc/images/templates/The_Burning_Crusade/statue-left.jpg" alt="">
    </div>

    <div class="wow2008-iron-frame"></div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const menuAssets = '/ascemu_tbc/images/menu/leftMenu/'
const navigation = [
  {
    key: 'news',
    title: 'News',
    icon: 'news',
    header: 'news',
    links: ['Current News', 'Archived News', 'Awards and Honors', 'Press Releases'],
  },
  {
    key: 'account',
    title: 'Account',
    icon: 'account',
    header: 'account',
    links: ['Create Account', 'Manage Account', 'Retrieve Password', 'Character Move', 'Paid Char Transfer', 'Recruit-A-Friend', 'Scroll of Resurrection', 'Parental Controls', 'Realm Status', 'Public Test Realm'],
  },
  {
    key: 'gameguide',
    title: 'Game Guide',
    icon: 'gameguide',
    header: 'gameguide',
    links: ['Game Guide', 'Introduction', 'Getting Started', 'Character', 'Reputations', 'Items', 'The World', 'Transportation', 'Player Interaction', 'Player vs Player', 'FAQ', 'Story', 'Burning Crusade', 'Wrath of the Lich King', 'Under Development', 'Previous Patches'],
  },
  {
    key: 'workshop',
    title: 'Workshop',
    icon: 'interactive',
    header: 'workshop',
    links: ['Armory', 'Arena', 'Encyclopedia', 'Talent Calculators', 'Events Calendar', 'Armor Sets', 'World Map', 'Battlegrounds'],
  },
  {
    key: 'media',
    title: 'Media',
    icon: 'media',
    header: 'media',
    links: ['Overview', 'Screenshots', 'Movies', 'Music', 'Wallpapers', 'Other Downloads', 'Gadgetzan Times', 'Blizzard Store', 'BlizzCast'],
  },
  {
    key: 'forums',
    title: 'Forums',
    icon: 'forums',
    header: 'forums',
    links: ['General', 'Class Forums', 'Realm Forums', 'Guild Recruitment', 'Guild Relations', 'Support'],
  },
  {
    key: 'community',
    title: 'Community',
    icon: 'community',
    header: 'community',
    links: ['Overview', 'Comics', 'Machinima', 'Community Spotlight', 'Contests', 'Guild Relations', 'Real-Life Events', 'Fan Art', 'Fan Sites', 'Fan Wallpapers'],
  },
  {
    key: 'support',
    title: 'Support',
    icon: 'support',
    header: 'support',
    links: ['Support News', 'Account Admin', 'Billing and Account', 'Technical Support', 'In-Game Support', 'Support Tools', 'Game Policies'],
  },
]

const openGroups = ref(['account'])
const toggleGroup = (key: string) => {
  openGroups.value = openGroups.value.includes(key)
    ? openGroups.value.filter(group => group !== key)
    : [...openGroups.value, key]
}

const quickLinks = [
  'Account Management',
  'Parental Controls',
  'Support Site',
  'Realm Status',
  'Account Creation',
  'Retrieve Password',
  'Account Security',
  'Latest Patch Notes',
  'Free 10-Day WoW Trial',
]
</script>

<style scoped>
.wow2008 {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  color: #17120a;
  font: 12px Arial, Helvetica, sans-serif;
  background: #000 url('/ascemu_tbc/images/templates/The_Burning_Crusade/page-bg.jpg') repeat-x center top;
}
.wow2008::before {
  content: '';
  position: absolute;
  top: 32px;
  left: 0;
  right: 0;
  height: 88px;
  z-index: 0;
  pointer-events: none;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/page-bg-top.jpg') no-repeat center top;
}
.wow2008 a {
  color: #1e4378;
  text-decoration: underline;
}
.wow2008-topbar {
  height: 32px;
  position: relative;
  z-index: 20;
  background: #072540 url('/ascemu_tbc/images/templates/The_Burning_Crusade/bg.gif') 50% 0 repeat-x;
  border-bottom: 1px solid #143352;
}
.wow2008-topbar__inner {
  width: 955px;
  max-width: 100%;
  height: 32px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 17px;
  box-sizing: border-box;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/topbg2.gif') no-repeat 50% 0;
}
.wow2008-topbar nav {
  display: flex;
  align-items: center;
  gap: 12px;
  height: 100%;
  white-space: nowrap;
}
.wow2008-topbar nav a {
  color: #fbb917;
  font: bold 11px Tahoma, Arial, sans-serif;
  text-decoration: none;
  text-shadow: 1px 1px #001027;
}
.wow2008-topbar__divider {
  display: block;
  width: 2px;
  height: 18px;
  background: linear-gradient(90deg, #172d46, #91a7b8 45%, #172d46);
}
.wow2008-search {
  height: 34px;
  display: flex;
  align-items: center;
  gap: 0;
  margin: 0;
}
.wow2008-search__left {
  width: 16px;
  height: 34px;
  background: url('/ascemu_tbc/images/layout/search/search-left.gif') no-repeat;
}
.wow2008-search__body {
  width: 396px;
  height: 34px;
  display: flex;
  align-items: center;
  background: url('/ascemu_tbc/images/layout/search/search-bg.gif') repeat-x;
}
.wow2008-search input {
  width: 230px;
  margin: 0 2px;
  padding: 2px 4px;
  height: 18px;
  border: 1px solid #7f7f7f;
  box-sizing: border-box;
  background: #040d1a;
  color: #ffac04;
}
.wow2008-search select {
  width: 112px;
  height: 20px;
  margin: 0 2px;
  border: 1px solid #7f7f7f;
  background: #040d1a;
  color: #ffac04;
  font-size: 10px;
}
.wow2008-search button {
  width: 55px;
  height: 19px;
  margin-left: 3px;
  border: 1px solid #8d5e17;
  background: #8d1f0b;
  color: #ffdb59;
  font: bold 10px Arial, sans-serif;
  cursor: pointer;
}
.wow2008-search__right {
  width: 8px;
  height: 34px;
  background: url('/ascemu_tbc/images/layout/search/search-right.gif') no-repeat;
}
.wow2008-stage {
  width: 1175px;
  max-width: none;
  min-height: 950px;
  margin: -85px auto 0;
  padding-top: 60px;
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 157px 1018px;
  align-items: stretch;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/menu-bg.jpg') repeat-y 65px 0;
}
.wow2008-header {
  position: absolute;
  top: -4px;
  left: -28px;
  z-index: 30;
  width: 252px;
  height: 103px;
}
.wow2008-logo,
.wow2008-logo img {
  display: block;
  width: 252px;
  height: 103px;
}
.wow2008-logo img {
  border: 0;
}
.wow2008-left {
  grid-column: 1;
  grid-row: 1;
  width: 157px;
  min-height: 900px;
  position: relative;
  top: 13px;
  margin: 0;
  padding: 0;
  background: transparent;
  box-sizing: border-box;
}
.wow2008-ne-top-left {
  position: absolute;
  top: -73px;
  left: -314px;
  width: 264px;
  height: 346px;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/ne-top-left.jpg') no-repeat;
  pointer-events: none;
}
.wow2008-ne-center {
  position: absolute;
  top: -73px;
  left: -50px;
  width: 61px;
  height: 578px;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/ne-center.jpg') no-repeat;
  pointer-events: none;
}
.wow2008-ne-bottom-left {
  position: absolute;
  top: 267px;
  left: -176px;
  width: 126px;
  height: 144px;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/ne-bottom-left.jpg') no-repeat;
  pointer-events: none;
}
.wow2008-ne-nav-bg {
  position: absolute;
  top: -23px;
  left: 11px;
  width: 142px;
  height: 528px;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/ne-nav-bg.jpg') no-repeat;
  pointer-events: none;
}
.wow2008-nav {
  width: 157px;
  position: relative;
  z-index: 4;
  margin: 39px 0 0;
  padding: 0;
  right: -16px;
  box-sizing: border-box;
}
.wow2008-nav-section {
  height: auto;
  min-height: 31px;
  margin: 0;
  padding: 0;
  position: relative;
}
.wow2008-nav-button {
  height: 27px;
  width: 142px;
  margin-top: 1px;
  position: relative;
  z-index: 2;
  cursor: pointer;
  background-repeat: no-repeat;
  background-position: 1px 0;
}
.wow2008-nav-button.menu-button-on {
  background-image: url('/ascemu_tbc/images/menu/leftMenu/leftMenu-button-on.gif');
}
.wow2008-nav-button.menu-button-off {
  background-image: url('/ascemu_tbc/images/menu/leftMenu/leftMenu-button-off.gif');
}
.wow2008-nav-icon {
  width: 24px;
  height: 21px;
  position: absolute;
  left: 5px;
  top: 3px;
  display: block;
  background-repeat: no-repeat;
}
.wow2008-nav-icon.is-wide {
  width: 25px;
}
.wow2008-nav-title {
  width: 105px;
  height: 25px;
  position: absolute;
  left: 30px;
  top: 1px;
  display: block;
  background-repeat: no-repeat;
  background-position: 0 5px;
}
.wow2008-nav-collapse {
  width: 15px;
  height: 14px;
  position: absolute;
  top: 9px;
  right: -2px;
  display: block;
  background-repeat: no-repeat;
  background-position: 0 0;
}
.wow2008-nav-collapse.is-open {
  background-image: url('/ascemu_tbc/images/leftmenu-minus.gif');
}
.wow2008-nav-collapse.is-closed {
  background-image: url('/ascemu_tbc/images/leftmenu-plus.gif');
}
.wow2008-nav-right-border {
  width: 9px;
  height: 35px;
  position: absolute;
  right: -10px;
  top: -4px;
  display: block;
  background: url('/ascemu_tbc/images/menu-add.gif') no-repeat 0 0;
}
.wow2008-nav-inner {
  width: 145px;
  position: relative;
  z-index: 2;
  padding: 0 0 0 4px;
  box-sizing: content-box;
}
.leftMenu-cont-top {
  width: 145px;
  height: 6px;
  background: url('/ascemu_tbc/images/leftMenu-cont-top.png') no-repeat 0 0;
}
.leftMenu-cont-mid {
  width: 145px;
  background: url('/ascemu_tbc/images/menu/mainmenu/leftMenu-back.png') repeat 0 0;
}
.leftMenu-cont-mid .m-left {
  background: url('/ascemu_tbc/images/leftMenu-cont-mid-left.jpg') repeat-y top left;
}
.leftMenu-cont-mid .m-left .m-right {
  background: url('/ascemu_tbc/images/leftMenu-cont-mid-right.jpg') repeat-y top right;
}
.leftMenu-cnt {
  padding-left: 5px;
}
.leftMenu-cont-bot {
  width: 145px;
  height: 8px;
  background: url('/ascemu_tbc/images/leftMenu-cont-bot.png') no-repeat 0 0;
}
.mainNav {
  list-style: none;
  margin: 0;
  padding: 0;
}
.mainNav li {
  margin: 0;
  padding: 0;
}
.wow2008-menu-entry {
  width: 139px;
  height: 15px;
  position: relative;
  left: -3px;
  margin: 0;
  padding: 0 0 0 10px;
  box-sizing: border-box;
  background: url('/ascemu_tbc/images/menu/mainmenu/bullet-trans-bg.gif') no-repeat 0 0;
  font: bold 11px/15px Arial, Helvetica, sans-serif;
}
.wow2008-menu-entry a,
.wow2008-menu-entry a:link,
.wow2008-menu-entry a:visited {
  display: block;
  width: 120px;
  color: #d0a803;
  font: bold 11px/15px Arial, Helvetica, sans-serif;
  text-decoration: none;
}
.wow2008-menu-entry a:hover {
  color: #fff;
}
.wow2008-center {
  grid-column: 2;
  grid-row: 1;
  width: 1018px;
  min-width: 0;
  min-height: 900px;
  position: relative;
  padding: 0;
  box-sizing: border-box;
  background: transparent;
}
.wow2008-main-top {
  height: 25px;
  width: 100%;
  position: relative;
  top: 0;
  z-index: 2;
  background: url('/ascemu_tbc/images/layout/frame_top-bg.jpg') repeat-x 0 0;
}
.wow2008-main-top > div {
  height: 25px;
  background: url('/ascemu_tbc/images/layout/frame_top-left.jpg') no-repeat top left;
}
.wow2008-main-top > div > div {
  height: 25px;
  background: url('/ascemu_tbc/images/layout/frame_top-right.jpg') no-repeat top right;
}
.wow2008-main-content-wrapper {
  min-height: 820px;
  background: url('/ascemu_tbc/images/layout/frame_left-bg.jpg') repeat-y 0 0;
}
.wow2008-main-content {
  min-height: 820px;
  background: url('/ascemu_tbc/images/layout/frame_right-bg.jpg') repeat-y top right;
}
.wow2008-content-padding {
  min-height: 820px;
  margin: 0 19px 0 17px;
  padding: 0;
  position: relative;
}
.wow2008-content-columns {
  display: grid;
  grid-template-columns: 735px 226px;
  align-items: start;
  column-gap: 0;
  margin: 3px 0 0 3px;
}
.wow2008-main-column {
  width: 735px;
  min-width: 0;
  margin: 0;
  padding: 0;
}
.wow2008-cnt-paper {
  width: 735px;
  background: url('/ascemu_tbc/images/layout/light.jpg') repeat 0 0;
}
.wow2008-cnt-top {
  height: 13px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-top.jpg') repeat-x top left;
}
.wow2008-cnt-top > div {
  height: 13px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-topleft.jpg') no-repeat top left;
}
.wow2008-cnt-top > div > div {
  height: 13px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-topright.jpg') no-repeat top right;
}
.wow2008-content-left {
  background: url('/ascemu_tbc/images/layout/cnt-paper-left.jpg') repeat-y top left;
}
.wow2008-content-right {
  min-height: 600px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-right.jpg') repeat-y top right;
}
.wow2008-cnt-main {
  min-height: 600px;
  padding: 0 12px 10px;
  background: url('/ascemu_tbc/images/layout/light.jpg') repeat 0 0;
}
.wow2008-cnt-bot {
  height: 7px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-bot.jpg') repeat-x bottom left;
}
.wow2008-cnt-bot > div {
  height: 7px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-botleft.jpg') no-repeat 0 100%;
}
.wow2008-cnt-bot > div > div {
  height: 7px;
  background: url('/ascemu_tbc/images/layout/cnt-paper-botright.jpg') no-repeat bottom right;
}
.wow2008-news-area {
  display: grid;
  grid-template-columns: 470px 226px;
  gap: 0;
  align-items: start;
  min-height: 750px;
  padding: 0;
  background: transparent;
  position: relative;
}
.wow2008-news-column {
  width: 470px;
  min-width: 0;
  padding: 0;
  margin: 0;
}
.wow2008-flash-container {
  width: 470px;
  height: 190px;
  position: relative;
  margin: 0 0 12px;
}
.wow2008-flash-placeholder {
  display: block;
  width: 474px;
  max-width: none;
  height: auto;
  position: relative;
  margin: 0 0 0 -2px;
}
.wow2008-news-heading {
  display: none;
}
.wow2008-news-column :deep(.topics) {
  padding: 0 4px;
}
.wow2008-news-column :deep(.topic-intro) {
  margin-bottom: 8px;
}
.wow2008-news-column :deep(.card) {
  border: 1px solid #c6a65d;
  background: #f5e6bd;
}
.wow2008-news-card {
  padding: 16px;
  background: #f1dfb4;
  border: 1px solid #c2a15b;
}
.wow2008-news-card h1 {
  font: 22px Georgia, serif;
  color: #17416a;
}
.wow2008-archive {
  width: 470px;
  height: 31px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: url('/ascemu_tbc/images/archives.jpg') no-repeat center top;
}
.wow2008-archive-button {
  display: block;
  width: 136px;
  height: 15px;
  background: url('/ascemu_tbc/images/news-archives.gif') no-repeat 0 0;
  line-height: 0;
  transform: translateY(-5px);
}
.wow2008-archive-button:hover,
.wow2008-archive-button:focus-visible,
.wow2008-archive-button:active {
  background-position: 0 -15px;
}
.wow2008-promo-grid {
  display: grid;
  grid-template-columns: repeat(3, 150px);
  gap: 10px;
  margin: 10px 0;
}
.wow2008-promo:nth-child(n + 2) {
  transform: translateX(1px);
}
.wow2008-promo {
  width: 150px;
  height: 123px;
  position: relative;
  display: block;
  margin: 0;
  padding: 0;
  color: #f2cf4b;
  text-decoration: none;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/community-smallteaser-bg.gif') no-repeat 0 0;
}
.wow2008-promo-frame {
  width: 150px;
  height: 123px;
  position: relative;
}
.wow2008-promo-frame > img {
  display: block;
  width: 133px;
  height: 93px;
  margin: 20px 0 0 7px;
  border: 0;
}
.wow2008-promo-icon {
  width: 36px;
  height: 36px;
  position: absolute;
  z-index: 2;
  top: -25px;
  left: -2px;
  background-repeat: no-repeat;
}
.wow2008-promo-icon--contest {
  background-image: url('/ascemu_tbc/images/visual-smallTeaser-contests.gif');
}
.wow2008-promo-icon--fanart {
  background-image: url('/ascemu_tbc/images/visual-smallTeaser-fanarts.gif');
}
.wow2008-promo-icon--wallpaper {
  top: -32px;
  height: 43px;
  background-image: url('/ascemu_tbc/images/visual-smallTeaser-wallp.gif');
}
.wow2008-promo-title {
  height: 20px;
  position: absolute;
  z-index: 2;
  top: -20px;
  left: 40px;
  width: 105px;
  margin: 0;
  padding: 0;
  background-repeat: no-repeat;
  background-position: 0 3px;
}
.wow2008-promo-title span {
  display: none;
}
.wow2008-promo-title--contest {
  background-image: url('/ascemu_tbc/images/header-contest.gif');
}
.wow2008-promo-title--fanart {
  background-image: url('/ascemu_tbc/images/header-fanarts.gif');
}
.wow2008-promo-title--wallpaper {
  background-image: url('/ascemu_tbc/images/header-wallpapers.gif');
}
.wow2008-read-more {
  width: 75px;
  height: 15px;
  position: absolute;
  z-index: 3;
  right: 6px;
  bottom: 28px;
  display: block;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/button-readmore.gif') no-repeat;
}
.wow2008-community {
  width: 470px;
  margin: 10px 0 12px;
  position: relative;
  color: #17120a;
  font: 11px/1.35 "Trebuchet MS", Arial, sans-serif;
}
.wow2008-community-top {
  height: 25px;
  position: relative;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/phatlootbox-top.gif') no-repeat 0 0;
}
.wow2008-community-heading {
  width: 120px;
  height: 27px;
  position: absolute;
  top: 5px;
  left: 38px;
  display: block;
  background: url('/ascemu_tbc/images/header-comm.gif') no-repeat 0 0;
}
.wow2008-community-heading h2 {
  width: 100%;
  height: 100%;
  margin: 0;
}
.wow2008-community-visual {
  width: 46px;
  height: 54px;
  position: absolute;
  z-index: 2;
  top: -9px;
  left: 0;
  display: block;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/visual-community.gif') no-repeat 0 0;
}
.wow2008-community-wrapper {
  min-height: 210px;
  padding: 0 12px 10px;
  background: url('/ascemu_tbc/images/community-bg.jpg') no-repeat 6px 100%, url('/ascemu_tbc/images/phatLootBox-bg.gif') repeat-y 0 0;
  box-sizing: border-box;
}
.wow2008-community .community-top {
  min-height: 25px;
  position: relative;
  padding: 3px 8px 0 10px;
  box-sizing: border-box;
}
.wow2008-community .community-top::before {
  content: "";
  position: absolute;
  z-index: 0;
  top: -3px;
  right: -7px;
  bottom: 0;
  left: -8px;
  background: url('/ascemu_tbc/images/phatLootBox-hdlbg.jpg') repeat-x 0 0;
}
.wow2008-community .community-top h3 {
  position: relative;
  z-index: 1;
  margin: 0;
  color: #fff;
  text-shadow: none;
  font: bold 12px/20px Georgia, "Times New Roman", serif;
}
.wow2008-community .community-top h3 i {
  color: #fff4cf;
  font: normal 10px Arial, sans-serif;
}
.wow2008-community .community-cnt {
  min-height: 175px;
  position: relative;
  padding: 9px 10px 8px;

  box-sizing: border-box;
}
.wow2008-community .community-cnt > p {
  margin: 0 0 8px;
  padding: 0 91px 0 0;
  color: #17120a;
  font: 11px/1.4 "Trebuchet MS", Arial, sans-serif;
}
.wow2008-community .community-cnt a {
  color: #17416a;
  text-decoration: underline;
}
.wow2008-community .community-cnt a:hover {
  color: #9b1c12;
}
.wow2008-community .community-cnt a:focus-visible,
.wow2008-community-heading:focus-visible,
.wow2008-community-visual:focus-visible,
.wow2008-community-read-more:focus-visible {
  outline: 1px dotted #f2cf4b;
  outline-offset: 2px;
}
.wow2008-community .community-portrait {
  width: 82px;
  height: 83px;
  float: right;
  position: relative;
  margin: 0 0 6px 9px;
}
.wow2008-community .community-portrait img {
  display: block;
  width: 64px;
  height: 64px;
  max-width: none;
  position: absolute;
  top: 8px;
  left: 8px;
  object-fit: cover;
}
.wow2008-community .community-portrait::after {
  content: "";
  width: 82px;
  height: 83px;
  position: absolute;
  inset: 0;
  z-index: 1;
  pointer-events: none;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/portrait-frame.gif') no-repeat 0 0;
}
.wow2008-community .community-watch {
  clear: both;
  margin: 8px 0 7px;
  padding: 7px 9px;
  color: #241b10;
  background: #e4d1a8;
  border: 1px solid #c5ad7c;
  font: 10px/1.35 "Trebuchet MS", Arial, sans-serif;
}
.wow2008-community .community-disclaimer {
  margin: 5px 0 8px;
  padding: 0;
  font-size: 9px;
}
.wow2008-community .blood {
  color: #6c1b12;
}
.wow2008-community .community-buttons ul {
  display: flex;
  gap: 8px;
  align-items: center;
  list-style: none;
  margin: 8px 0 0;
  padding: 0 0 0 5px;
}
.wow2008-community .community-buttons li {
  margin: 0;
  padding: 0;
}
.wow2008-community .redButton-container {
  height: 22px;
  display: flex;
  align-items: stretch;
  white-space: nowrap;
}
.wow2008-community .community-button-left,
.wow2008-community .community-button-right {
  height: 22px;
  flex: 0 0 auto;
  display: block;
  background-repeat: no-repeat;
}
.wow2008-community .community-button-left {
  width: 5px;
  background-image: url('/ascemu_tbc/images/templates/The_Burning_Crusade/button-left.gif');
}
.wow2008-community .community-button-right {
  width: 7px;
  background-image: url('/ascemu_tbc/images/templates/The_Burning_Crusade/button-right.gif');
}
.wow2008-community .community-button-label {
  width: 110px;
  height: 22px;
  position: relative;
  display: block;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/button-center.gif') repeat-x 0 0;
  text-align: center;
  font: bold 11px/22px Arial, sans-serif;
}
.wow2008-community .community-button-label a,
.wow2008-community .community-button-label .rdbtn_sh {
  width: 110px;
  height: 22px;
  position: absolute;
  inset: 0;
  display: block;
  color: #fff4cf;
  text-decoration: none;
}
.wow2008-community .community-button-label .rdbtn_sh {
  display: none;
}
.wow2008-community .community-button-label a {
  z-index: 1;
  text-shadow: 1px 1px 1px #3b0905, -1px 0 #3b0905, 0 1px #3b0905;
}
.wow2008-community-bottom {
  height: 28px;
  position: relative;
  background: url('/ascemu_tbc/images/phatLootBox-bottom.jpg') no-repeat 0 -1px;
}
.wow2008-community-read-more {
  width: 75px;
  height: 15px;
  position: absolute;
  right: 6px;
  bottom: 16px;
  display: block;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/button-readmore.gif') no-repeat 0 0;
}
.wow2008-banner-row {
  display: grid;
  grid-template-columns: 226px 226px;
  gap: 8px;
  margin: 12px 0 18px;
}
.wow2008-banner {
  width: 226px;
  height: 91px;
  position: relative;
  display: block;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/service-smallteaser-bg.gif') no-repeat 0 0;
}
.wow2008-banner--help {
  background-image: url('/ascemu_tbc/images/templates/The_Burning_Crusade/service-smallteaser-bg.gif'), url('/ascemu_tbc/images/needhelp-bg.jpg');
  background-repeat: no-repeat, no-repeat;
  background-position: 0 0, 8px 22px;
}
.wow2008-banner--jobs {
  transform: translateX(12px);
  background-image: url('/ascemu_tbc/images/templates/The_Burning_Crusade/service-smallteaser-bg.gif'), url('/ascemu_tbc/images/jobs-bg.jpg');
  background-repeat: no-repeat, no-repeat;
  background-position: 0 0, 8px 22px;
}
.wow2008-banner-read-more {
  width: 75px;
  height: 15px;
  position: absolute;
  z-index: 3;
  right: 8px;
  bottom: 8px;
  display: block;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/button-readmore.gif') no-repeat 0 0;
}
.wow2008-banner-icon {
  width: 36px;
  height: 35px;
  position: absolute;
  z-index: 2;
  top: -4px;
  left: 0;
  background-repeat: no-repeat;
}
.wow2008-banner-icon--help {
  background-image: url('/ascemu_tbc/images/visual-smallTeaser-needhelp.gif');
}
.wow2008-banner-icon--jobs {
  background-image: url('/ascemu_tbc/images/visual-smallTeaser-jobs.gif');
}
.wow2008-banner-label {
  height: 20px;
  position: absolute;
  top: 3px;
  left: 38px;
  width: 105px;
  background-repeat: no-repeat;
}
.wow2008-banner-label--help {
  background-image: url('/ascemu_tbc/images/header-needhelp.gif');
}
.wow2008-banner-label--jobs {
  background-image: url('/ascemu_tbc/images/header-jobs.gif');
}
.wow2008-link-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px 16px;
  padding: 0 5px 20px;
}
.wow2008-link-group {
  min-height: 75px;
  border: 0;
}
.wow2008-link-group h3 {
  height: 29px;
  margin: -13px 0 7px;
  padding: 0 8px;
  display: flex;
  align-items: center;
  position: relative;
  box-sizing: border-box;
  background: none;
  color: #173d63;
  font: bold 10px/1 Georgia, "Times New Roman", serif;
  isolation: isolate;
  z-index: 1;
  transform: translateY(3px);
}
.wow2008-link-group h3::before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 1px;
  left: 0;
  width: 100%;
  height: 29px;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/miscbox-top.gif') repeat-x 0 0;
  pointer-events: none;
}
.wow2008-link-group h3 span {
  position: relative;
  z-index: 1;
  transform: translate(12px, 10px);
  color: #fff;
}
.wow2008-link-group ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.wow2008-link-group li {
  min-height: 14px;
  padding-left: 12px;
  line-height: 14px;
  background: url('/ascemu_tbc/images/icons/bullet.gif') no-repeat 0 3px;
}
.wow2008-link-group li a {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 9px;
  font-weight: bold;
  color: #1e4378;
  text-decoration: underline;
  background-color: transparent;
}
.wow2008-link-group p {
  margin: 0 0 4px;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 12px;
  line-height: normal;
}
.wow2008-right {
  width: 226px;
  min-width: 0;
  margin: 0 0 0 -1px;
  padding: 0;
  position: relative;
}
.wow2008-bc-upgrade {
  width: 213px;
  margin: 0 auto 12px;
  position: relative;
}
.wow2008-bc-upgrade h2 {
  height: 27px;
  margin: 0;
  background: url('/ascemu_tbc/images/templates/The_Burning_Crusade/marginal-infobox-top.jpg') no-repeat 43px 0;
}
.wow2008-bc-upgrade h2 img {
  width: 121px;
  height: auto;
  display: block;
  margin-left: 48px;
}
.wow2008-bc-upgrade__content {
  min-height: 95px;
  display: flex;
  align-items: flex-start;
  gap: 8px;
  padding: 6px 9px;
  background: url('/ascemu_tbc/images/marginal-infoBox-bg.gif') repeat-y 0 0;
  box-sizing: border-box;
  font: 11px/1.25 Arial, sans-serif;
}
.wow2008-bc-upgrade__content > img {
  width: 55px;
  height: 91px;
  object-fit: contain;
}
.wow2008-bc-upgrade__content strong,
.wow2008-bc-upgrade__content span,
.wow2008-bc-upgrade__content a {
  display: block;
  margin-bottom: 4px;
}
.wow2008-bc-upgrade__content a {
  padding: 2px 5px;
  color: #f9df85;
  text-align: center;
  background: #8c260d;
  font-size: 10px;
  font-weight: bold;
}
.wow2008-quicklinks,
.wow2008-screenshot,
.wow2008-newcomers {
  width: 213px;
  margin: 0 auto 12px;
  position: relative;
}
.wow2008-marginal-top {
  width: 213px;
  height: 27px;
  position: relative;
  background: url('/ascemu_tbc/images/marginal-infoBox-top-ie.jpg') no-repeat 43px 0;
}
.wow2008-marginal-top h2 {
  height: 20px;
  margin: 0;
  position: absolute;
  top: 5px;
  left: 30px;
  width: 150px;
  background-repeat: no-repeat;
  background-position: 0 0;
}
.wow2008-quicklinks .wow2008-marginal-top h2 {
  background-image: url('/ascemu_tbc/images/header-quick_links.jpg');
}
.wow2008-screenshot .wow2008-marginal-top h2 {
  background-image: url('/ascemu_tbc/images/header-ssotd.gif');
}
.wow2008-newcomers .wow2008-marginal-top h2 {
  background-image: url('/ascemu_tbc/images/header-newcomers.jpg');
}
.wow2008-marginal-icon {
  position: absolute;
  z-index: 3;
  top: -14px;
  left: -3px;
  width: 46px;
  height: 54px;
  background-repeat: no-repeat;
}
.wow2008-marginal-icon--quicklinks {
  background-image: url('/ascemu_tbc/images/visual-infoBox-bg.gif');
}
.wow2008-marginal-icon--ssotd {
  top: -6px;
  background-image: url('/ascemu_tbc/images/visual-infoBox-ssotd.gif');
}
.wow2008-marginal-icon--newcomers {
  top: -6px;
  background-image: url('/ascemu_tbc/images/visual-infoBox-ng.gif');
}
.wow2008-marginal-body {
  width: 213px;
  box-sizing: border-box;
  padding: 0 8px 6px;
  background: url('/ascemu_tbc/images/marginal-infoBox-bg.gif') repeat-y 0 0;
}
.wow2008-quicklinks ul {
  list-style: none;
  margin: 0;
  padding: 0 10px 5px;
}
.wow2008-quicklinks li {
  margin: 0 10px 0 0;
  padding: 3px 0;
  border-bottom: 1px solid #af9771;
}
.wow2008-quicklinks a {
  display: block;
  padding-left: 20px;
  color: #1e4378;
  font: bold 11px Arial, sans-serif;
  background: url('/ascemu_tbc/images/icons/bullet.gif') no-repeat 0 40%;
  text-decoration: none;
}
.wow2008-quicklinks a:hover {
  color: #c60000;
}
.wow2008-marginal-bottom {
  height: 10px;
  background: url('/ascemu_tbc/images/marginal-infoBox-bottom.gif') no-repeat 0 0;
}
.wow2008-screenshot-body {
  padding: 0 8px 6px;
  background: #050607 url('/ascemu_tbc/images/marginal-infoBox-bg.gif') repeat-y 0 0;
}
.wow2008-screenshot__image {
  width: 197px;
  height: 125px;
  background: #030405 url('/ascemu_tbc/images/visual-infoBox-ssotd.gif') no-repeat 0 0;
}
.wow2008-screenshot select {
  width: 179px;
  height: 17px;
  display: block;
  margin: 3px auto 0;
  border: 1px solid #835a20;
  background: #ae813e;
  color: #17120a;
  font-size: 10px;
}
.wow2008-newcomers-body {
  width: 213px;
  padding: 7px 10px 8px;
  box-sizing: border-box;
  background: url('/ascemu_tbc/images/marginal-infoBox-bg.gif') repeat-y 0 0;
  color: #17120a;
  font: 10px/1.25 Arial, sans-serif;
}
.wow2008-newcomers-entry {
  min-height: 67px;
  margin: 0 0 6px;
  position: relative;
  padding-left: 65px;
}
.wow2008-newcomers-entry img {
  position: absolute;
  top: 0;
  left: 0;
  width: 58px;
  height: 58px;
  object-fit: cover;
}
.wow2008-newcomers-entry strong,
.wow2008-newcomers-entry span {
  display: block;
}
.wow2008-newcomers-button {
  display: block;
  width: 103px;
  margin: 4px auto 0;
  padding: 3px 6px;
  text-align: center;
  color: #ffdc50 !important;
  background: #7d1c08;
  border: 2px ridge #9b793e;
  text-decoration: none !important;
  font-weight: bold;
}
.wow2008-main-bottom {
  height: 41px;
  width: 100%;
  position: relative;
  z-index: 10;
  margin-bottom: -16px;
  background: url('/ascemu_tbc/images/layout/frame_bottom-bg.jpg') repeat-x 0 0;
}
.wow2008-main-bottom > div {
  height: 41px;
  background: url('/ascemu_tbc/images/layout/frame_bottom-left.jpg') no-repeat top left;
}
.wow2008-main-bottom > div > div {
  height: 41px;
  background: url('/ascemu_tbc/images/layout/frame_bottom-right.jpg') no-repeat top right;
}
.wow2008-blizz-logo {
  position: relative;
  display: block;
  top: -61px;
  text-align: center;
  z-index: 500;
}
.wow2008-blizz-logo img {
  width: 97px;
  height: 57px;
  position: relative;
}
.wow2008-statue-left {
  width: 243px;
  height: 445px;
  position: absolute;
  left: -185px;
  bottom: 41px;
  z-index: 2;
  pointer-events: none;
}
.wow2008-iron-frame {
  width: 100%;
  height: 20px;
  margin-top: -2px;
  position: relative;
  z-index: 0;
  background: #000 url('/ascemu_tbc/images/templates/The_Burning_Crusade/ironframe-bg.jpg') repeat-x top;
}
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
}
@media (max-width: 1175px) {
  .wow2008 {
    width: 1175px;
    zoom: calc(100vw / 1175);
  }

  .wow2008-stage {
    margin-left: 0;
    margin-right: 0;
  }
}
</style>

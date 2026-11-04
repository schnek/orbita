<template>
  <div class="wow2008">
    <div class="wow2008-topbar">
      <div class="wow2008-topbar__inner">
        <nav aria-label="External links">
          <a href="#">WorldofWarcraft.com</a>
          <a href="#">The Armory</a>
          <a href="#">Forums</a>
        </nav>
        <form class="wow2008-search" role="search" @submit.prevent>
          <label class="visually-hidden" for="wow-search">Search</label>
          <input id="wow-search" type="search">
          <select aria-label="Search area">
            <option>Community Site</option>
            <option>World of Warcraft</option>
          </select>
          <button type="submit">Search</button>
        </form>
      </div>
    </div>

    <div class="wow2008-stage">
      <div class="wow2008-frame">
      <header class="wow2008-header">
        <a class="wow2008-logo" href="/" aria-label="World of Warcraft home">
          <img src="/wow2008/images/templates/The_Burning_Crusade/wowlogo-front.gif" alt="World of Warcraft">
        </a>
      </header>

      <div class="wow2008-layout">
        <aside class="wow2008-left" aria-label="Main navigation">
          <div class="wow2008-character-art" aria-hidden="true"><span class="wow2008-ne-top-left"></span><span class="wow2008-ne-center"></span><span class="wow2008-ne-bottom-left"></span></div>
          <nav class="wow2008-nav">
            <section v-for="group in navigation" :key="group.key" class="wow2008-nav__group">
              <div class="wow2008-nav__heading">
                <img class="wow2008-nav__icon" :src="`${themeAssets}icon-${group.asset}-${openGroups.includes(group.key) ? 'on' : 'off'}.gif`" alt=""><img class="wow2008-nav__title" :src="`${themeAssets}header-${group.asset}-${openGroups.includes(group.key) ? 'on' : 'off'}.gif`" :alt="group.title">
                <button type="button" :aria-expanded="openGroups.includes(group.key)" :aria-label="`Toggle ${group.title}`" @click="toggleGroup(group.key)">
                  <img :src="`${themeAssets}leftmenu-button-${openGroups.includes(group.key) ? 'on' : 'off'}.gif`" alt="">
                </button>
              </div>
              <ul v-if="openGroups.includes(group.key)">
                <li v-for="link in group.links" :key="link"><a href="#">{{ link }}</a></li>
              </ul>
            </section>
          </nav>
        </aside>

        <main class="wow2008-center">
          <div class="wow2008-news-area">
            <div class="wow2008-news-column">
              <img class="wow2008-flash-placeholder" src="/wow2008/images/no-flash.jpg" alt="Welcome to World of Warcraft.com">
              <div class="wow2008-news-heading">Latest News</div>
              <slot>
                <article class="wow2008-news-card">
                  <h1>Welcome to World of Warcraft</h1>
                  <p>Connect your Orbita news topics to publish announcements here.</p>
                </article>
              </slot>
              <div class="wow2008-archive"><a href="#">View News Archives</a></div>

              <div class="wow2008-promo-grid">
                <a class="wow2008-promo wow2008-promo--contest" href="#"><strong>Contests</strong><b>More</b></a>
                <a class="wow2008-promo wow2008-promo--fanart" href="#"><strong>Fan Art</strong><b>More</b></a>
                <a class="wow2008-promo wow2008-promo--wallpaper" href="#"><strong>Wallpapers</strong><b>More</b></a>
              </div>

              <section class="wow2008-community">
                <h2>Community</h2>
                <div class="wow2008-community__title">Community Spotlight <span>• News and creations</span></div>
                <div class="wow2008-community__body">
                  <p>Discover artwork, stories, screenshots and creations from the World of Warcraft community.</p>
                  <p class="wow2008-community__note">Have something you would like to share with the community? Send us a link.</p>
                  <div class="wow2008-community__actions"><a href="#">Warcraft Weekly</a><a href="#">Spotlight Archive</a></div>
                </div>
              </section>

              <div class="wow2008-banner-row">
                <a class="wow2008-banner wow2008-banner--help" href="#" aria-label="Need Help"></a>
                <a class="wow2008-banner wow2008-banner--jobs" href="#" aria-label="Jobs"></a>
              </div>

              <div class="wow2008-link-grid">
                <section class="wow2008-link-group">
                  <h3>WoW: Wrath of the Lich King</h3>
                  <ul><li><a href="#">Bestiary</a></li><li><a href="#">Dragonblight</a></li><li><a href="#">Screenshots</a></li><li><a href="#">Features</a></li><li><a href="#">Movies</a></li></ul>
                </section>
                <section class="wow2008-link-group">
                  <h3>Movies and Trailers</h3>
                  <ul><li><a href="#">Sunwell Plateau</a></li><li><a href="#">Verne Troyer</a></li><li><a href="#">M.P.T.</a></li><li><a href="#">William Shatner</a></li></ul>
                </section>
                <section class="wow2008-link-group">
                  <h3>World of Warcraft Insider</h3>
                  <p>Your number one source of up-to-date, behind the scenes information about World of Warcraft!</p>
                  <ul><li><a href="#">Latest issue</a></li><li><a href="#">Subscribe now</a></li></ul>
                </section>
                <section class="wow2008-link-group">
                  <h3>Online Store</h3>
                  <ul><li><a href="#">World of Warcraft Battle Chest</a></li><li><a href="#">World of Warcraft 2008 Daily Calendar</a></li><li><a href="#">Burning Crusade Strategy Guide</a></li><li><a href="#">TCG: Onyxia Raid Deck</a></li></ul>
                </section>
              </div>
            </div>

            <aside class="wow2008-right">
              <a class="wow2008-expansion-banner" href="#">Wrath of the Lich King</a>
              <section class="wow2008-quicklinks">
                <h2>Quick Links</h2>
                <ul>
                  <li v-for="link in quickLinks" :key="link"><a href="#">{{ link }}</a></li>
                </ul>
              </section>
              <section class="wow2008-screenshot">
                <h2>Screenshot of the Day</h2>
                <div class="wow2008-screenshot__image" role="img" aria-label="Screenshot of the day"></div>
              </section>
            </aside>
          </div>
          <footer class="wow2008-footer"><img src="/wow2008/images/templates/The_Burning_Crusade/statue-left.jpg" alt="" class="wow2008-statue-left"><img src="/wow2008/images/new/bot-blizzlogo.gif" alt="Blizzard Entertainment"></footer>
        </main>
      </div>
      </div>
    </div>
    <div class="wow2008-bottom-bar"></div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const themeName = 'The Burning Crusade'
const themeAssets = '/wow2008/images/templates/The_Burning_Crusade/'
const navigation = [
 {key:'news',asset:'news',title:'News',links:['Current News','Archived News','Awards and Honors','Press Releases']},
 {key:'account',asset:'account',title:'Account',links:['Create Account','Manage Account','Retrieve Password','Character Move','Paid Char Transfer','Recruit-A-Friend','Scroll of Resurrection','Parental Controls','Realm Status','Public Test Realm']},
 {key:'gameguide',asset:'gameguide',title:'Game Guide',links:['Game Guide','Introduction','Getting Started','Character','Reputations','Items','The World','Transportation','Player Interaction','Player vs Player','FAQ','Story','Burning Crusade','Wrath of the Lich King','Under Development','Previous Patches']},
 {key:'community',asset:'community',title:'Community',links:['Community News','Contests','Fan Art']},
 {key:'forums',asset:'forums',title:'Forums',links:['Forums','Guild Forums']},
 {key:'media',asset:'media',title:'Media',links:['Screenshots','Wallpapers','Movies']},
 {key:'support',asset:'support',title:'Support',links:['Support','Submit a Ticket','Known Issues']},
 {key:'workshop',asset:'interactive',title:'Workshop',links:['Armory','Arena','Encyclopedia','Talent Calculators','Events Calendar','Armor Sets']},
]
const openGroups = ref(['news','account','gameguide'])
const toggleGroup = (key:string) => { openGroups.value = openGroups.value.includes(key) ? openGroups.value.filter(x => x !== key) : [...openGroups.value,key] }
const quickLinks = ['Account Management','Parental Controls','Support Site','Realm Status','Account Creation','Retrieve Password','Account Security','Latest Patch Notes','Free 10-Day WoW Trial']
</script>

<style scoped>
.wow2008{min-height:100vh;background:#000 url('/wow2008/images/templates/The_Burning_Crusade/page-bg.jpg') center top repeat-x;color:#17120a;font:12px Arial,Helvetica,sans-serif;overflow:hidden;position:relative}
.wow2008:before{content:"";position:absolute;z-index:0;top:0;left:0;right:0;height:180px;background:url('/wow2008/images/templates/The_Burning_Crusade/page-bg-top2.jpg') center top repeat-x;pointer-events:none}
.wow2008 a{color:#003c80;text-decoration:underline}
.wow2008-topbar{height:32px;background:#072540 url('/wow2008/images/templates/The_Burning_Crusade/bg.gif') center top repeat-x;position:relative;z-index:10;border-bottom:1px solid #143352}
.wow2008-topbar__inner{height:32px;width:1175px;margin:0 auto;display:flex;align-items:center;justify-content:space-between;padding:0 12px;box-sizing:border-box}
.wow2008-topbar nav{display:flex;align-items:center;gap:12px;height:100%;white-space:nowrap}
.wow2008-topbar nav a{color:#d5e7ff;font:bold 11px Tahoma,Arial,sans-serif;text-decoration:none;text-shadow:1px 1px #001027}
.wow2008-topbar nav a+a:before{content:"";display:inline-block;width:2px;height:18px;margin:0 12px 0 0;vertical-align:middle;background:linear-gradient(90deg,#172d46,#91a7b8 45%,#172d46)}
.wow2008-search{display:flex;gap:4px;align-items:center}.wow2008-search input{width:120px;background:#080b10;color:#fff;border:1px solid #7189a4}.wow2008-search select,.wow2008-search button{height:22px;background:#172b45;color:#e4edfa;border:1px solid #7189a4;font-size:10px}
.wow2008-stage{width:1175px;margin:0 auto;display:grid;grid-template-columns:475px 700px;position:relative;align-items:stretch;z-index:1}
.wow2008-frame{display:contents}
.wow2008-header{position:absolute;z-index:12;top:-32px;left:475px;width:700px;height:105px;pointer-events:none;background:url('/wow2008/images/templates/The_Burning_Crusade/topbg2.gif') center 32px no-repeat}
.wow2008-logo{pointer-events:auto;position:absolute;top:0;left:-90px;width:252px;height:103px;display:block;background:url('/wow2008/images/templates/The_Burning_Crusade/wowlogo-wrathtrans.gif') left top no-repeat}
.wow2008-logo img{display:block;width:252px;height:103px;object-fit:contain}
.wow2008-layout{display:contents}
.wow2008-left{grid-column:1;grid-row:1;width:475px;min-height:900px;position:relative;background:#000 url('/wow2008/images/templates/The_Burning_Crusade/ne-nav-bg.jpg') 11px 0 no-repeat;box-sizing:border-box}
.wow2008-character-art{height:578px;width:475px;position:relative;background:none}.wow2008-ne-top-left{position:absolute;top:-73px;left:-314px;width:264px;height:346px;background:url('/wow2008/images/templates/The_Burning_Crusade/ne-top-left.jpg') no-repeat}.wow2008-ne-center{position:absolute;top:-73px;left:-50px;width:64px;height:578px;background:url('/wow2008/images/templates/The_Burning_Crusade/ne-center.jpg') no-repeat}.wow2008-ne-bottom-left{position:absolute;top:267px;left:-176px;width:144px;height:126px;background:url('/wow2008/images/templates/The_Burning_Crusade/ne-bottom-left.jpg') no-repeat}
.wow2008-left{background:none}
.wow2008-nav{position:absolute;top:13px;left:11px;width:157px;min-height:546px;margin:0;padding:0 8px 30px;background:url('/wow2008/images/templates/The_Burning_Crusade/ne-nav-bg.jpg') no-repeat;box-sizing:border-box;z-index:2}
.wow2008-nav__group{margin:0}.wow2008-nav__heading{height:27px;display:flex;align-items:center;position:relative}
.wow2008-nav__heading{height:27px;display:flex;align-items:center;position:relative}.wow2008-nav__icon{position:absolute;left:5px;top:3px;width:24px;height:21px}.wow2008-nav__title{position:absolute;left:30px;top:6px;width:105px;height:14px;object-fit:contain;object-position:left center}
.wow2008-nav__heading button{position:absolute;right:0;top:2px;width:22px;height:22px;padding:0;border:0;background:transparent;cursor:pointer}
.wow2008-nav__heading button img{display:block;width:22px;height:22px}.wow2008-nav__heading button{background:url('/wow2008/images/templates/The_Burning_Crusade/leftmenu-button-off.gif') no-repeat 1px 0}.wow2008-nav__heading button[aria-expanded="true"]{background-image:url('/wow2008/images/templates/The_Burning_Crusade/leftmenu-button-on.gif')}
.wow2008-nav ul{list-style:none;margin:0 0 5px;padding:3px 3px 5px 22px;background:rgba(0,0,0,.2)}.wow2008-nav__group{position:relative}.wow2008-nav__group:before{content:"";position:absolute;inset:0;background:url('/wow2008/images/templates/The_Burning_Crusade/menu-bg.jpg') repeat-y;opacity:.25;pointer-events:none}
.wow2008-nav li{line-height:16px}.wow2008-nav a{color:#e4d4a0;text-decoration:none;font-size:11px}
.wow2008-center{grid-column:2;grid-row:1;width:700px;min-width:0;position:relative;padding:0 14px 70px;background:#ead3a5 url('/wow2008/images/blog-content-bg.jpg') repeat;box-sizing:border-box;min-height:900px}
.wow2008-center:before,.wow2008-center:after{content:"";position:absolute;top:0;bottom:0;width:14px;z-index:5;pointer-events:none}
.wow2008-center:before{left:0;background:url('/wow2008/images/ss-border-left.gif') repeat-y left top}
.wow2008-center:after{right:0;background:url('/wow2008/images/ss-border-right.gif') repeat-y right top}
.wow2008-news-area{display:grid;grid-template-columns:minmax(0,1fr) 175px;gap:8px;min-height:800px;padding:100px 8px 20px;background:#ead3a5 url('/wow2008/images/blog-content-bg.jpg') repeat;position:relative}
.wow2008-news-area:before{content:"";position:absolute;top:0;left:0;right:0;height:20px;background:url('/wow2008/images/blog-content-top.jpg') repeat-x}
.wow2008-news-column{padding:0 0 0 5px;min-width:0}.wow2008-flash-placeholder{display:block;width:100%;max-width:474px;height:auto;margin:0 auto 10px}
.wow2008-news-heading{display:none}.wow2008-news-column :deep(.topics){padding:0 4px}.wow2008-news-column :deep(.topic-intro){margin-bottom:8px}.wow2008-news-column :deep(.card){border:1px solid #c6a65d;background:#f5e6bd}
.wow2008-news-card{padding:16px;background:#f1dfb4;border:1px solid #c2a15b}.wow2008-news-card h1{font:22px Georgia,serif;color:#17416a}
.wow2008-archive{text-align:center;padding:9px;border-top:1px solid #b99b62}.wow2008-archive a{font-size:10px;text-transform:uppercase;background:#eee0bc;padding:2px 12px}
.wow2008-promo-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin:10px 0}
.wow2008-promo{height:90px;position:relative;display:flex;flex-direction:column;justify-content:space-between;padding:5px;color:#f2cf4b!important;text-decoration:none!important;background-color:#10151b}
.wow2008-promo strong,.wow2008-banner strong{font:bold 13px Georgia,serif;text-shadow:1px 1px #000}.wow2008-promo b,.wow2008-banner b{align-self:flex-end;background:#6e1308;padding:2px 12px;font-size:9px}
.wow2008-promo--contest{background:url('/wow2008/images/visual-smallTeaser-contests.gif') center/cover no-repeat}.wow2008-promo--fanart{background:url('/wow2008/images/visual-smallTeaser-fanarts.gif') center/cover no-repeat}.wow2008-promo--wallpaper{background:url('/wow2008/images/visual-smallTeaser-wallp.gif') center/cover no-repeat}
.wow2008-community{margin:10px 0;background:#e7d5ad url('/wow2008/images/templates/The_Burning_Crusade/community-smallteaser-bg.gif') no-repeat}.wow2008-community h2,.wow2008-quicklinks h2,.wow2008-screenshot h2{margin:0;padding:4px 6px 4px 42px;color:#e9bd31;font:bold 14px Georgia,serif;background:#17283a url('/wow2008/images/templates/The_Burning_Crusade/header-generalnews.gif') no-repeat 38px 5px}
.wow2008-community__title{padding:6px 9px;background:#071a30;color:#f2cb45;font-weight:bold}.wow2008-community__title span{color:#8bd3ee;font-style:italic;font-size:10px}
.wow2008-community__body{padding:12px;color:#17120a;font-size:11px;line-height:1.35}.wow2008-community__note{padding:8px;background:#dfc99a;border:1px solid #c2a675}
.wow2008-community__actions{display:flex;justify-content:center;gap:8px}.wow2008-community__actions a{background:#4c1009;color:#ffd33c;padding:4px 12px;text-decoration:none}
.wow2008-banner-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:12px 0}
.wow2008-banner{height:86px;display:block;position:relative;background:url('/wow2008/images/templates/The_Burning_Crusade/service-smallteaser-bg.gif') no-repeat left top}
.wow2008-banner--help:before,.wow2008-banner--jobs:before{content:"";display:block;position:absolute;top:0;left:0;width:100%;height:100%;background-repeat:no-repeat;background-position:0 0;pointer-events:none}
.wow2008-banner--help:before{background-image:url('/wow2008/images/visual-smallTeaser-needhelp.gif')}
.wow2008-banner--jobs:before{background-image:url('/wow2008/images/visual-smallTeaser-wallp.gif')}
.wow2008-link-grid{display:grid;grid-template-columns:1fr 1fr;gap:18px 12px;padding:0 5px 20px}.wow2008-link-group{min-height:75px;border-top:2px solid #8b7549}
.wow2008-link-group h3{margin:-10px 0 7px;padding:0 5px;display:table;background:#ead3a5;color:#173d63;font:bold 12px Georgia,serif}.wow2008-link-group ul{margin:0;padding-left:18px}.wow2008-link-group li{line-height:14px}.wow2008-link-group p{margin:0 0 4px;font-size:11px}
.wow2008-right{padding:0}.wow2008-expansion-banner{height:80px;display:flex;align-items:flex-end;justify-content:center;padding:5px;color:#f2d36c!important;font:bold 12px Georgia,serif;text-decoration:none!important;background:#081b32 url('/wow2008/images/page-bg-alt3_2.jpg') center/cover no-repeat}
.wow2008-quicklinks{margin:10px 0;padding-top:24px;background:#e7d2a4 url('/wow2008/images/templates/The_Burning_Crusade/marginal-infobox-top-ql.gif') no-repeat 43px 0}.wow2008-quicklinks ul{list-style:none;margin:0;padding:6px 10px}.wow2008-quicklinks li{padding:5px 0;border-bottom:1px solid #c0a979}.wow2008-quicklinks a{font-size:11px;font-weight:bold}
.wow2008-screenshot{background:#07090a;padding:24px 2px 2px;background-image:url('/wow2008/images/templates/The_Burning_Crusade/marginal-infobox-top.jpg');background-repeat:no-repeat;background-position:43px 0}.wow2008-screenshot__image{height:130px;background:#030405 url('/wow2008/images/visual-infoBox-ssotd.gif') center/cover no-repeat}
.wow2008-footer{height:70px;position:absolute;bottom:0;left:0;right:0;display:flex;justify-content:center;align-items:center;background:url('/wow2008/images/bottom-bg.gif') repeat-x;z-index:6}
.wow2008-footer img:not(.wow2008-statue-left){width:150px;height:auto;object-fit:contain}
.wow2008-statue-left{position:absolute;left:-14px;bottom:0;width:90px;height:auto}
.wow2008-bottom-bar{height:0}
@media(max-width:1180px){.wow2008-stage{width:100%;grid-template-columns:minmax(220px,40%) minmax(0,700px)}.wow2008-left{width:100%}.wow2008-center{width:100%}}
@media(max-width:700px){.wow2008-stage{display:block}.wow2008-left{width:100%;min-height:0}.wow2008-character-art{display:none}.wow2008-nav{width:auto;display:grid;grid-template-columns:1fr 1fr}.wow2008-center{width:100%;padding:12px 10px 70px}.wow2008-news-area{display:block}.wow2008-right{padding:8px;display:grid;grid-template-columns:1fr 1fr}.wow2008-screenshot{display:none}.wow2008-logo{left:10px;top:-50px;transform:scale(.7);transform-origin:top left}}
</style>
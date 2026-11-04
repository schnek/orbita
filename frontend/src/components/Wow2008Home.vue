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

    <div class="wow2008-frame">
      <header class="wow2008-header">
        <a class="wow2008-logo" href="/" aria-label="World of Warcraft home">
          <img src="/wow2008/images/wowlogo-horde.gif" alt="World of Warcraft Community Site">
        </a>
      </header>

      <div class="wow2008-layout">
        <aside class="wow2008-left" aria-label="Main navigation">
          <div class="wow2008-character-art" aria-hidden="true"></div>
          <nav class="wow2008-nav">
            <section v-for="group in navigation" :key="group.title" class="wow2008-nav__group">
              <h2><span class="wow2008-nav__crest"></span>{{ group.title }}</h2>
              <ul>
                <li v-for="link in group.links" :key="link"><a href="#">{{ link }}</a></li>
              </ul>
            </section>
          </nav>
        </aside>

        <main class="wow2008-center">
          <div class="wow2008-news-area">
            <div class="wow2008-news-column">
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
                <a class="wow2008-banner wow2008-banner--help" href="#"><strong>Need Help</strong><span>Support related issues</span><b>More</b></a>
                <a class="wow2008-banner wow2008-banner--jobs" href="#"><strong>Jobs</strong><span>Blizzard is hiring!</span><b>More</b></a>
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
          <footer class="wow2008-footer"><img src="/wow2008/images/bottom-blizzlogo.gif" alt="Blizzard Entertainment"></footer>
        </main>
      </div>
    </div>
    <div class="wow2008-bottom-bar"></div>
  </div>
</template>

<script setup lang="ts">
const navigation = [
  {title: 'News', links: ['Current News', 'Archived News', 'Awards and Honors', 'Press Releases']},
  {title: 'Account', links: ['Create Account', 'Manage Account', 'Retrieve Password', 'Character Move', 'Paid Char Transfer', 'Recruit-A-Friend', 'Scroll of Resurrection', 'Parental Controls', 'Realm Status', 'Public Test Realm']},
  {title: 'Game Guide', links: ['Game Guide', 'Introduction', 'Getting Started', 'Character', 'Reputations', 'Items', 'The World', 'Transportation', 'Player Interaction', 'Player vs Player', 'FAQ', 'Story', 'Burning Crusade', 'Wrath of the Lich King', 'Under Development', 'Previous Patches']},
  {title: 'Workshop', links: ['Armory', 'Arena', 'Encyclopedia', 'Talent Calculators', 'Events Calendar', 'Armor Sets']},
]
const quickLinks = ['Account Management', 'Parental Controls', 'Support Site', 'Realm Status', 'Account Creation', 'Retrieve Password', 'Account Security', 'Latest Patch Notes', 'Free 10-Day WoW Trial']
</script>

<style scoped>
.wow2008{min-height:100vh;background:#050505;color:#17120a;font:12px Arial,Helvetica,sans-serif;overflow:hidden}
.wow2008 a{color:#003c80;text-decoration:underline}
.wow2008-topbar{height:39px;background:linear-gradient(#050b12 0%,#101a24 55%,#392b19 58%,#070707 100%);border-bottom:4px ridge #6c6048;color:#e6b800}
.wow2008-topbar__inner{max-width:930px;height:35px;margin:auto;display:flex;align-items:center;justify-content:flex-end;gap:24px}
.wow2008-topbar nav{display:flex;gap:28px;font-weight:bold}
.wow2008-topbar nav a{color:#f2c300;text-decoration:none}
.wow2008-search{display:flex;gap:4px;align-items:center}
.wow2008-search input{width:150px;background:#080b10;border:2px inset #777;color:#fff;height:22px}
.wow2008-search select,.wow2008-search button{height:22px;background:#17120c;color:#f5c400;border:1px solid #8d6d32;font-size:10px}
.wow2008-frame{width:930px;min-height:calc(100vh - 43px);margin:0 auto;position:relative;background:#17130f url('/wow2008/images/page-bg.jpg') repeat;border-left:5px ridge #6f654d;border-right:5px ridge #6f654d;box-shadow:0 0 20px #000}
.wow2008-header{height:78px;position:relative;background:#080b10 url('/wow2008/images/page-bg-alt3_1.jpg') center top/cover no-repeat;border-bottom:5px ridge #766443}
.wow2008-logo{position:absolute;z-index:2;top:0;left:-24px;width:184px;height:94px;text-decoration:none!important;background:transparent}.wow2008-logo img{display:block;width:184px;height:94px}
.wow2008-logo__world,.wow2008-logo__warcraft,.wow2008-logo__expansion{display:block;font-family:Georgia,serif;font-weight:bold;line-height:.9}
.wow2008-logo__world{font-size:21px;letter-spacing:4px;margin-top:15px}
.wow2008-logo__warcraft{font-size:30px;color:#e7bd4b;-webkit-text-stroke:1px #211509}
.wow2008-logo__expansion{font-size:10px;color:#f4d66b;margin-top:5px}
.wow2008-layout{display:grid;grid-template-columns:155px 1fr;gap:8px;min-height:900px;padding:0 8px 0 0;background:linear-gradient(90deg,#080908 0 155px,#5b492a 155px,#e5d1a5 160px,#e7d4aa 100%)}
.wow2008-left{position:relative;min-height:900px;padding-top:0;background:#080a0b url('/wow2008/images/orc-nav-bg.jpg') center top repeat-y;border-right:3px ridge #8a754d}
.wow2008-character-art{height:340px;margin-top:0;background:#080b0d url('/wow2008/images/orc-center.jpg') center top no-repeat;position:relative}

.wow2008-nav{position:relative;z-index:1;margin-top:-10px}
.wow2008-nav__group{margin:0 0 6px;border:2px ridge #827044;background:linear-gradient(90deg,#050607,#10151b);box-shadow:0 1px 4px #000}
.wow2008-nav__group h2,.wow2008-community h2,.wow2008-quicklinks h2,.wow2008-screenshot h2{margin:0;padding:4px 6px;color:#e9bd31;font: bold 14px Georgia,serif;text-shadow:1px 1px #000;background:linear-gradient(90deg,#071322,#17283a 75%,#07090d);border-bottom:1px solid #9d844a}
.wow2008-nav__crest{display:inline-block;width:17px;height:17px;margin-right:5px;vertical-align:middle;border-radius:50%;background:radial-gradient(circle,#d7b54c,#25200e 65%,#080808);border:1px solid #a78c45}
.wow2008-nav ul{list-style:none;margin:0;padding:4px 7px 6px 13px}
.wow2008-nav li{line-height:15px}
.wow2008-nav a{color:#e3bd00;text-decoration:none;font-weight:bold;font-size:11px;text-shadow:1px 1px #000}
.wow2008-nav a:before{content:'· ';color:#d5a900}
.wow2008-center{min-width:0;position:relative;padding:14px 8px 0 4px;background:linear-gradient(90deg,#6b552f 0,#e9d6aa 8px,#e8d4a8 98%,#70572e 100%)}
.wow2008-news-area{display:grid;grid-template-columns:minmax(0,1fr) 208px;gap:9px;min-height:850px;padding:0 0 20px;background:#e8d5aa url('/wow2008/images/page-bg-alt4.jpg') center top/cover repeat-y;border:1px solid #9e824d;box-shadow:inset 0 0 12px #b49a69}
.wow2008-news-column{padding:215px 0 0 10px;min-width:0}
.wow2008-news-heading{display:none}
.wow2008-news-column :deep(.topics){padding:0 4px}
.wow2008-news-column :deep(.topic-intro){margin-bottom:8px}
.wow2008-news-column :deep(.card){border:1px solid #c6a65d;background:#f5e6bd}
.wow2008-news-card{padding:16px;background:#f1dfb4;border:1px solid #c2a15b}
.wow2008-news-card h1{font:22px Georgia,serif;color:#17416a}
.wow2008-archive{text-align:center;padding:9px;border-top:1px solid #b99b62}
.wow2008-archive a{font-size:10px;text-transform:uppercase;background:#eee0bc;padding:2px 12px}
.wow2008-promo-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:10px 0}
.wow2008-promo,.wow2008-banner{height:100px;position:relative;display:flex;flex-direction:column;justify-content:space-between;padding:5px;color:#f2cf4b!important;text-decoration:none!important;border:3px ridge #9a7840;background-color:#10151b;box-shadow:0 2px 4px #604d2b}
.wow2008-promo strong,.wow2008-banner strong{font: bold 13px Georgia,serif;text-shadow:1px 1px #000}
.wow2008-promo span{align-self:center;color:#fff;font-weight:bold;text-shadow:1px 1px #000}
.wow2008-promo b,.wow2008-banner b{align-self:flex-end;background:#6e1308;padding:2px 12px;font-size:9px;text-transform:uppercase}
.wow2008-promo--contest{background:url('/wow2008/images/visual-smallTeaser-contests.gif') center/cover no-repeat}
.wow2008-promo--fanart{background:url('/wow2008/images/visual-smallTeaser-fanarts.gif') center/cover no-repeat}.wow2008-promo--wallpaper{background:url('/wow2008/images/visual-smallTeaser-wallp.gif') center/cover no-repeat}
.wow2008-community{margin:10px 0;border:3px ridge #927646;background:#e7d5ad;box-shadow:0 2px 4px #79633e}
.wow2008-community h2{font-size:15px}
.wow2008-community__title{padding:6px 9px;background:#071a30;color:#f2cb45;font-weight:bold}
.wow2008-community__title span{color:#8bd3ee;font-style:italic;font-size:10px}
.wow2008-community__body{padding:12px;color:#17120a;font-size:11px;line-height:1.35}
.wow2008-community__note{padding:8px;background:#dfc99a;border:1px solid #c2a675}
.wow2008-community__actions{display:flex;justify-content:center;gap:8px}
.wow2008-community__actions a{background:#4c1009;border:2px ridge #ad873e;color:#ffd33c;padding:4px 12px;text-decoration:none}
.wow2008-banner-row{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:12px 0 18px}
.wow2008-banner{height:70px}
.wow2008-banner--help{background:url('/wow2008/images/needhelp-bg.jpg') center/cover no-repeat}
.wow2008-banner--jobs{background:url('/wow2008/images/jobs-bg.jpg') center/cover no-repeat}
.wow2008-link-grid{display:grid;grid-template-columns:1fr 1fr;gap:22px 16px;padding:0 5px 20px}
.wow2008-link-group{min-height:75px;border-top:2px solid #8b7549}
.wow2008-link-group h3{margin:-10px 0 7px;padding:0 5px;display:table;background:#e8d5aa;color:#173d63;font:bold 12px Georgia,serif}
.wow2008-link-group ul{margin:0;padding-left:18px;list-style:disc}
.wow2008-link-group li{line-height:14px}
.wow2008-link-group p{margin:0 0 4px;font-size:11px}
.wow2008-right{padding:135px 5px 0 0}
.wow2008-expansion-banner{height:88px;display:flex;align-items:flex-end;justify-content:center;padding:5px;color:#f2d36c!important;font:bold 12px Georgia,serif;text-decoration:none!important;text-shadow:1px 1px #000;border:4px ridge #887044;background:#081b32 url('/wow2008/images/page-bg-alt3_2.jpg') center/cover no-repeat;box-shadow:0 2px 4px #65502e}
.wow2008-quicklinks{margin:10px 0 14px;border:4px ridge #9a7845;background:#e7d2a4;box-shadow:0 2px 5px #5b4829}
.wow2008-quicklinks h2,.wow2008-screenshot h2{font-size:13px}
.wow2008-quicklinks ul{list-style:none;margin:0;padding:6px 10px}
.wow2008-quicklinks li{padding:5px 0;border-bottom:1px solid #c0a979}
.wow2008-quicklinks a{font-size:11px;font-weight:bold}
.wow2008-quicklinks a:before{content:'✦';display:inline-block;width:20px;color:#174c79}
.wow2008-screenshot{border:3px ridge #987b48;background:#07090a;padding:2px}
.wow2008-screenshot__image{height:145px;background:#030405 url('/wow2008/images/visual-infoBox-ssotd.gif') center/cover no-repeat}
.wow2008-footer{height:55px;display:flex;align-items:center;justify-content:center;margin:0 auto;background:#08090a url('/wow2008/images/bottom-bg.gif') center top repeat-x}.wow2008-footer img{width:auto;max-width:none;height:auto;max-height:100%;object-fit:contain}
.wow2008-bottom-bar{height:18px;background:linear-gradient(#292b2d,#090a0b 45%,#62543b 48%,#111);border-top:4px ridge #756548}
@media(max-width:950px){.wow2008-frame{width:100%;}.wow2008-topbar__inner{padding:0 10px}.wow2008-layout{grid-template-columns:145px minmax(0,1fr)}.wow2008-news-area{grid-template-columns:minmax(0,1fr) 185px}}
@media(max-width:700px){.wow2008-topbar nav{display:none}.wow2008-search{margin-left:auto}.wow2008-frame{border:0}.wow2008-layout{display:block;padding:0}.wow2008-left{min-height:0;padding:100px 8px 8px;border:0}.wow2008-character-art{display:none}.wow2008-nav{display:grid;grid-template-columns:1fr 1fr;gap:5px}.wow2008-nav__group{margin:0}.wow2008-center{padding:8px}.wow2008-news-area{display:block}.wow2008-news-column{padding:8px}.wow2008-right{padding:8px;display:grid;grid-template-columns:1fr 1fr;gap:8px}.wow2008-screenshot{display:none}.wow2008-expansion-banner{height:70px}.wow2008-promo-grid{gap:4px}.wow2008-promo{height:75px;padding:3px}.wow2008-promo strong{font-size:11px}.wow2008-link-grid{gap:15px 8px}}
</style>
---
title: Changelog
date: 2021-02-21
thumbnail: /images/uploads/changelog.jpg
---

## 1.0 beta - 21 February 2021

#### New Features

* Added first three episodes
* Site launch

#### Add images to home page links

* Add new field for tile image in file:   pages\p\_page.vue
* Change BaelGrid.vue page to accomodate a tile image.   


          <nuxt-link
            class="xs-text-center xs-flex xs-full-height xs-flex-align-center xs-flex-justify-center xs-text-center"
            :to="p.path"
          ><img :src="p.tile" :alt="p.title"/></nuxt-link>


          <nuxt-link
            class="xs-text-center xs-flex xs-full-height xs-flex-align-center xs-flex-justify-center xs-text-center"
            :to="p.path"
          >{{p.title}}</nuxt-link>
		  
		  
		  

# photos-module

## Prerequisites
<ul>
	<li><a target="_blank" href="https://getbootstrap.com/">Boostrap4</a></li>
	<li><a target="_blank" href="https://feimosi.github.io/baguetteBox.js/">Baguette Box JS</a></li>
</ul>

## Step 1: Add the Form
 - photo-form.tpl

Create a calendar for the Photo Gallery and upload the following form. This module must be a "Type" of "Photos", which will allow you to upload photos to each gallery. Be sure to replace SITE_NAME with your site's name.

```
<div class="panel-group">
  <div class="panel panel-default">
    <div class="panel-heading">
      <h4 class="panel-title"><a aria-expanded="true" data-toggle="collapse" href="#collapseStatus">Post Status<span
            class="toggle" aria-hidden="true"></span></a></h4>
    </div>

    <div class="panel-collapse collapse in" id="collapseStatus">
      <div class="panel-body">
        <div class="row">
          <div class="col-md-3">
            <h2><label class="label-control" for="post_status">Post Status</label></h2>
            <select class="form-control" name="post_status" type="text">
              <option value="Draft">Draft</option>
              <option value="Published">Published</option>
            </select>
          </div>

          <div class="col-md-3">
            <h2><label class="label-control" for="post_author">Post Author</label></h2>
            <select class="form-control" name="post_author" type="text">
              <option value="None">None</option>
              <option value="AUTHOR_NAME">AUTHOR_NAME</option>
            </select>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="panel-group">
  <div class="panel panel-default">
    <div class="panel-heading">
      <h4 class="panel-title"><a aria-expanded="true" data-toggle="collapse" href="#collapseImages">Photo Album <span
            class="toggle" aria-hidden="true"></span></a></h4>
    </div>

    <div class="panel-collapse collapse in" id="collapseImages">
      <div class="panel-body">
        <div class="row">
          <div class="col-md-4">
            <h2><label class="label-control" for="featured_image">Featured Image</label></h2>
            <input class="file_upload" id="featured_image" name="featured_image" required="" type="file" />
          </div>
          <div class="col-md-4">
            <h2><label class="label-control" for="heading_title">Album Name</label></h2>
            <input class="form-control" id="heading_title" name="heading_title" required="" type="text" />
          </div>
          <div class="col-md-4">
            <h2><label class="label-control" for="photo_album_intro">Album Intro</label></h2>
            <input class="form-control" id="photo_album_intro" name="photo_album_intro" type="text" />
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="panel-group">
  <div class="panel panel-default">
    <div class="panel-heading">
      <h4 class="panel-title"><a data-toggle="collapse" href="#collapseMeta">META Data <span class="toggle" aria-hidden="true"></span></a></h4>
    </div>

    <div class="panel-collapse collapse" id="collapseMeta">
      <div class="panel-body">
        <div class="row">
          <div class="col-md-12">
            <h2><label name="meta_title">Meta Title</label></h2>

            <p class="subText">(Optional) Include a custom META Title that will show in your browser tab and in the
              page's source code.</p>
            <input class="form-control" id="meta_title" name="meta_title" type="text" />
          </div>
        </div>

        <div class="row">
          <div class="col-md-12">
            <h2><label name="meta_description">Meta Description</label></h2>

            <p class="subText">(Optional) Include a custom META Description that search engines will index. 50-160
              Characters</p>
            <textarea class="form-control" id="meta_description" name="meta_description"></textarea>
          </div>
        </div>

        <div class="row">
          <div class="col-md-12">
            <h2><label name="meta_keywords">Meta Keywords</label></h2>

            <p class="subText">(Optional) Include the main keywords of the blog article.</p>
            <textarea class="form-control" id="meta_keywords" name="meta_keywords"></textarea>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="panel-group">
  <div class="panel panel-default">
    <div class="panel-heading">
      <h4 class="panel-title"><a data-toggle="collapse" href="#collapseAdvanced">Advanced <span class="toggle"
            aria-hidden="true"></span></a></h4>
    </div>

    <div class="panel-collapse collapse" id="collapseAdvanced">
      <div class="panel-body">
        <div class="row">
          <div class="col-md-12">
            <h2><label class="label-control" for="post_javascript">Custom JavaScript</label></h2>

            <p class="subText">(Optional) Use the following textbox to embed any custom JavaScript including tracking
              pixels and Google Analytics scripts. Be sure to open your JavaScript with a &lt;script&gt; tag and close
              everything with a &lt;/script&gt; tag.</p>
            <textarea class="form-control" id="post_javascript" name="post_javascript"></textarea>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
<?php
        if(isset($dataVars['calendar_entry_id'])){     
          $calendar_entry = new Calendar_Entry($dataVars['calendar_entry_id']);
          if($calendar_entry->path) { 
      ?>

<div class="panel-group">
  <div class="panel panel-default">
    <div class="panel-heading">
      <h4 class="panel-title"><a data-toggle="collapse" href="#collapseURL">Post URL <span class="toggle" aria-hidden="true"></span></a></h4>
    </div>

    <div class="panel-collapse collapse in" id="collapseURL">
      <div class="panel-body">
        <div class="row">
          <div class="col-md-12">
            <p class="subText">You can access this blog post at the following URL:</p>
            <a href="https://www.SITE_NAME.com<?= $calendar_entry->path ?>" target="_blank">https://www.SITE_NAME.com
              <?= $calendar_entry->path ?></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
<?php 
          } 
        }
       ?>

```

## Step 2: Add the Repeater
 - photo-repeater.tpl

Add the following repeater shortcode. 

```
<div class="row pt-3">
<div class="col-md-8 mx-auto text-md-center">
<p>The cosmos is full of indescribable beauty, and our talented photographers are telling our story through images.
Explore the breathtaking visual backdrop to the LunarXP mission.</p>
</div>
</div>
<div class="row py-5">
  [repeater id='8' pages="22" order="start_time desc" display_type="news" where="post_status='Published'"]
  <div class="col-sm-6 col-md-4">
    <div class="bg-light-gray bg-hover-light-gray-dark pointer box-sizing h-100">
      <a href="{{path}}" class="text-black">
        <img class="w-100 h-200p cover img-fluid" alt="{{heading_title}} Gallery" src="[get_asset_file_url id={{featured_image}}]">
        <div class="p-3 p-lg-4">
          <h2 class="h3 mt-2 text-secondary">
            [is_set value="{{heading_title}}"]
            {{heading_title}}
            [/is_set]
            [is_empty value="{{heading_title}}"]
            {{event_title}}
            [/is_empty]
          </h2>
          <p class="post-intro lead-sm">{{photo_album_intro}}</p>
          <p class="text-primary small"><strong>[print_date format="F d, Y" timestamp="{{start_time}}"]</strong></p>
        </div>
      </a>
    </div>
  </div>
  [/repeater]
</div> 
```

## Step 3: Add the Detail Template
- photo-detail.tpl

```
[entry]

<p>{{photo_album_intro}}</p>
<div class="row mt-5 bag-gallery">
[calendar_entry_attachments_repeat id="{{calendar_entry_id}}"]
  <div class="col-sm-6 col-md-4">
    <a aria-label="Image {{{asset_file_id}}} Link" href="[get_asset_file_url id='{{{asset_file_id}}}']" data-caption="{{{description}}}">
      <img class="w-100 cover h-200p" src="[get_asset_file_url id='{{{asset_file_id}}}']" alt="Image {{{asset_file_id}}} Link">
    </a>
  </div>
[/calendar_entry_attachments_repeat] 
</div>
{{post_javascript}}
[/entry]

```

## Step 4: Add the SCSS/SCC
  - /_/scss/photos.scss

```
.bg-hover-light-gray-dark {
    &:hover {
        background-color: #e1e1e1 !important;
    }
}

.pointer {
    cursor: pointer;
}

.h-200p {
    height: 200px;
}

.cover {
    object-fit: cover;
}
```

## Step 5: Add the JS
  - /_/js/photos.js
  
```
window.onload = function() {

    // Detect IE
    function detectIE() {
      var ua = window.navigator.userAgent;
  
      var msie = ua.indexOf('MSIE ');
      if (msie > 0) {
        // IE 10 or older => return version number
        return parseInt(ua.substring(msie + 5, ua.indexOf('.', msie)), 10);
      }
  
      var trident = ua.indexOf('Trident/');
      if (trident > 0) {
        // IE 11 => return version number
        var rv = ua.indexOf('rv:');
        return parseInt(ua.substring(rv + 3, ua.indexOf('.', rv)), 10);
      }
  
      var edge = ua.indexOf('Edge/');
      if (edge > 0) {
        // Edge (IE 12+) => return version number
        return parseInt(ua.substring(edge + 5, ua.indexOf('.', edge)), 10);
      }
  
      // other browser
      return false;
    }
  
  
    var isIE = detectIE();
    
    if (isIE != false) {

      var obCoverImgs = document.querySelectorAll('.cover');
      var imgLength;
      imgLength = obCoverImgs.length;
      var thisParent;
      var newDiv;
      var thisSRC;

      for (var i = 0; i < imgLength; i++) {

        thisSRC = obCoverImgs[i].src;
        thisParent = obCoverImgs[i].parentNode;

        if (thisSRC) {

          obCoverImgs[i].className += " hidden";

          newDiv = document.createElement("div");
          newDiv.className = "image-hero-container";

          newDiv.style.backgroundImage = "url('" + thisSRC + "')";
          
          // If image is using height classes, take those for the containing div. These will override the fallback of height on page load.
          for (var j = 0; j < obCoverImgs[i].classList.length; j++) {
            if (obCoverImgs[i].classList[j].match(/^h-/)) {
              newDiv.className += " " + obCoverImgs[i].classList[j];
            }
          }
          newDiv.style.height = obCoverImgs[i].clientHeight + "px";


          newDiv.appendChild(obCoverImgs[i]);
          thisParent.insertBefore(newDiv, thisParent.firstChild);

        }
      }
    }
      /** ===========================================
     # Initialize Photo Gallery
  ============================================ */
    baguetteBox.run('.bag-gallery');
};

```

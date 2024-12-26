![saplings >](https://github.com/kanopi/saplings/assets/5177009/a6377e32-deb2-49d8-873a-f3dd5a36fa7c)

# Adding a Language Switcher to Saplings

1. Add Language Switcher (Content) block to the Block Layout in the Programmatically Placed region.
2. Add a modal to the page.html.twig template with the block placed in it with twig tweak

```
<div id="language-switcher-modal" class="modal-container-outside settlein-modal">
 <!-- Modal content -->
 <div class="video-modal-container">
   <div class="modal-content">
     <div class="modal-header">
       <button class="close">{{ 'Close Modal'|t }}</button>
     </div>
     <div class="modal-body">
       <h2>{{ 'Choose your language'|t }}</h2>
       {{ drupal_entity('block', 'saplings_child_languageswitchercontent') }}
     </div>
   </div>
 </div>
</div>
```

3. Add a tb-megamenu-nav.html.twig template file to add a language switcher button

```
<ul {{ attributes }} >
 {% for li in lis %}
   {{ li }}
 {% endfor %}
</ul>
<button type="button" class="modal-language-switcher btn btn-secondary btn-icon btn-icon-before btn-icon-after btn-icon-translate w-100 justify-content-center" data-bs-target="#language-switcher-modal" aria-label="Open Language Switcher">{{ 'Language'|t }}</button>
```

4. Add js to toggle open/close the language switcher

```
/**
* Language Switcher JS.
* @file
*/
(function (Drupal, drupalSettings) {
   /*
   * Get language switcher modal.
   */
   Drupal.behaviors.languageModal = {
       attach: function (context) {
         // Get the button that opens the modal
         var btn = document.querySelectorAll(".modal-language-switcher");
          // Div to insert modal content into
         var modalContainer = document.querySelector('#language-switcher-modal');
          for (var i = 0; i < btn.length; i++) {
           btn[i].addEventListener('click', function () {
             modalContainer.style.display = "block";
           });
         }
          // When the user clicks on <span> (x), close the modal
         document.querySelector("#language-switcher-modal .close").onclick = function() {
           modalContainer.style.display = "none";   
         }
          // When the user clicks anywhere outside of the modal, close it
         window.onclick = function(event) {
           if (event.target.classList.contains('video-modal-container')) {
               modalContainer.style.display = "none";
             }
         }
       },
     };
 })(Drupal, drupalSettings);
 ```

5. Add styles to the modal

```
// Styles for Language Switcher Modal
#language-switcher-modal {
 h2 {
   margin-bottom: 2.5rem;
 }
 ul.links {
   list-style: none;
   padding: 0;
   margin: 0;
   display: grid;
   gap: 1rem;
   grid-template-columns: repeat(4, 1fr);


   @include media-breakpoint-down(md) {
     grid-template-columns: repeat(2, 1fr);
     overflow: scroll;
   }


   li {


     a {
       background-color: $settle-light-green;
       padding: 2rem 1.5rem;
       border-radius: 1.5rem;
       display: block;
       font-weight: 700;
       border: 1px solid transparent;
       color: $settle-darker-green;


       &:hover {
         opacity: 1;
         background-color: #D9EEDF;
       }


       &:active, &.is-active {
         border: 1px solid $settle-green;
       }
     }
   }
 }
}


.modal-language-switcher {
 &::after {
   content: '\F282' !important;
 }
}
header {
 .modal-language-switcher {
   @include media-breakpoint-down(xl) {
     display: none;
   }
 }
}
```

6. To get each language to display in it’s own Language (Español not Spanish), in /admin/config/regional/language, Edit each language and update the Language name to be the translated version.

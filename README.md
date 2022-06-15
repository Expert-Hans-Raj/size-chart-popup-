# size-chart-popup-

# 1 To open a popup in the product-template.liquid, you need to add the following trigger to the Section directory:

{%- when 'size-chart'-%}
        {% if block.settings.show_sizechart %}
        <div class="size_chart" {{ block.shopify_attributes }}>
          {% if product.options contains 'Size' %} 
          <a href="#size-chart" class="popup-trigger" data-popup-trigger="one" >
            <img src="https://cdn.shopify.com/s/files/1/0609/5047/9012/files/meter.png?v=1655102814"/> Size Chart
          </a> 
          {% endif %}
        </div>
         {% render 'size-chart'%}
         {% endif %}


#  2. Click the Snippet directory and add new snippet file with size-chart.liqued file & copy my code paste under size-chart.liqued file.

.<div class="body-blackout"></div>
<div class="popup-modal shadow" data-popup-modal="one">
  <div class="popup-modal__close">X</div>
  {% if section.settings.show_img %}
  {% for image in product.images  %}
  {% if image.alt contains  "sizechart" %}
 <img src="{{ image | img_url : "original"}}"/>
 {% endif %}
  {% endfor %}

  {% else  %} 
  {{ pages.size-chart.content }}

  {% endif %}
</div>
<script src="{{ 'popup.js' | asset_url }}" defer="defer"></script>


# 3 Create PopUp.js file & Enter the following code to add a new asset popup.js in the Assets directory:


const modalTriggers = document.querySelectorAll('.popup-trigger')
const modalCloseTrigger = document.querySelector('.popup-modal__close')
const bodyBlackout = document.querySelector('.body-blackout')

modalTriggers.forEach(trigger => {
  trigger.addEventListener('click', () => {
    const { popupTrigger } = trigger.dataset
    const popupModal = document.querySelector(`[data-popup-modal="${popupTrigger}"]`)

    popupModal.classList.add('is--visible')
    bodyBlackout.classList.add('is-blacked-out')
    
    popupModal.querySelector('.popup-modal__close').addEventListener('click', () => {
       popupModal.classList.remove('is--visible')
       bodyBlackout.classList.remove('is-blacked-out')
    })
    
    bodyBlackout.addEventListener('click', () => {
      popupModal.classList.remove('is--visible')
      bodyBlackout.classList.remove('is-blacked-out')
    })
  })
})



# 5. Click the Assets directory to open your css file

# 6. At the bottom of the file add styles for the popup:

/*================ Popup ================*/
body {
	position: relative;
}

.body-blackout {
  position: absolute;
  z-index: 1010;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .65);
  display: none;
}
.body-blackout.is-blacked-out {
  display: block;
}

.popup-trigger {
  display: inline-block;
}

.popup-modal {
  background-color: #fff;
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  padding: 45px;
  opacity: 0;
  pointer-events: none;
  transition: all 300ms ease-in-out;
  z-index: 1011;
}

.popup-modal.is--visible {
  opacity: 1;
  pointer-events: auto;
}

.popup-modal__close {
  position: absolute;
  font-size: 25px;
  right: 6px;
  top: 3px;
  cursor: pointer;
}


# 7 To open a popup in the product-template.liquid, you need to add the block under blocks:

{
  "type":"size-chart",
  "name":"Size Chart",
  "settings":[
   {
      "type": "checkbox",
      "id": "show_sizechart",
      "label":"Show Size Chart",
      "default":false
    }
  ]
  }
# 8 add setting & section settings:- 

   {
      "type": "checkbox",
      "id": "show_img",
      "label":"Show Size Chart as a Image",
      "default":false,
      "info":"By default Show, size chart page on all products, if product contain size option. If you want to show different size chart on specific products then you need to add size chart image on under product media with image alt tag 'sizechart'"
    }

# 9 Open theme.liqued file and find global.js file & then add below Jquery CDN:- 
 <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
 
 
 
 
 Please use my code & contact me, If you facing any issue.
 
 # Contact:-  ecommerce.web.expert@gmail.com
 
 
 Demo Url:- 
 
 # https://teenasboutique.com/
 # https://exactlystyle.myshopify.com/

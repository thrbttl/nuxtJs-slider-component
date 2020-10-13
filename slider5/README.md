# COMPONENTS

````nuxtJs
<Slider :sliderData="sliderData" />
````
````nuxtJs
import Slider from '../node_modules/nuxtjslider/slider5/Slider'
`````
````nuxtJs
sliderData: {
        images: ["image/1.jpg", "image/2.jpg", "image/3.jpg"],
        content : {
          title : "lorem ipsum",
          subTitle : "Lorem ipsum, dolor sit amet consectetur adipisicing elit. Et fugit non sapiente ex nesciunt ratione.",
          btn1: "Whatch More",
          btn2: "Deneme"
        },
        color : {
          titleColor : "",
          subTitleColor : "",
        },
        path : {
          btn1Path : "deneme1",
          btn2Path : "deneme2"
        }
      }
````

slide scale text stable
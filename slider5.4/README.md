# COMPONENTS

```nuxtJs
<Slider :sliderData="sliderData" />
```

```nuxtJs
import Slider from '../node_modules/nuxtjslider/slider5.1/Slider'
```

```nuxtJs
sliderData: {
        images: ["image/1.jpg", "image/2.jpg", "image/3.jpg", "image/4.jpg"],
        titleArray: ["deneme1", "deneme2", "deneme3", "deneme4"],
        subTitleArray: [
          "1 Lorem ipsum, dolor sit amet consectetur adipisicing elit. Et fugit non sapiente ex nesciunt ratione.",
          "2 Lorem ipsum, dolor sit amet consectetur adipisicing elit. Et fugit non sapiente ex nesciunt ratione.",
          "3 Lorem ipsum, dolor sit amet consectetur adipisicing elit. Et fugit non sapiente ex nesciunt ratione.",
          "4 Lorem ipsum, dolor sit amet consectetur adipisicing elit. Et fugit non sapiente ex nesciunt ratione.",
        ],
        pathArray: ["deneme1", "deneme2", "deneme3", "deneme4"],
        btn: "More",
        color: {
          titleColor: "red",
          subTitleColor: "white",
          backgroundColor: "#090d36"
        },
      },
```

slide left right opacty
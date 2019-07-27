How to add a new skin
=====================

Follow the informations to create your own skin.
```less
// build/less/variables.less
@ticketing: rgb(61, 164, 171);
```

```less
// build/less/alerts.less
.alert-ticketing {
  &:extend(.bg-ticketing);
  border-color: darken(@ticketing, 5%);
}
```

```less
// build/less/miscllaneous.less
.bg-ticketing {
  background-color: @ticketing !important;
  color: #FFF;
}

.bg-ticketing-active {
  background-color: darken(@ticketing , 3%) !important;
}

.text-ticketing {
  color: @ticketing !important;
}

.bg-ticketing-gradient {
  .gradient(@ticketing; @ticketing; lighten(@ticketing, 10%)) !important;
  color: #fff;
}
```

Almost done, you now need to create the skin file. For this step, copy an existing skin file and remplace the color with your own.

```bash
cp build/less/skins/skin-red.less build/less/skins/skin-ticketing.less
// Replace @red by @ticketing
```

Add your skin to the _all-skins.less
```
// build/less/skins/_all-skins.less.less
@import "skin-ticketing.less";
```

Add you skin to the Gruntfile.js
````js
// Gruntfile.js
grunt.initConfig({
    //...
    less: {
        //...
        skins: {
            files: {
                //...
                'dist/css/skins/skin-ticketing.css' : 'build/less/skins/skin-ticketing.less'
                //...
            }        
        },
        minifiedSkins: {
            files: {
                //...
               'dist/css/skins/skin-ticketing.min.css' : 'build/less/skins/skin-ticketing.less',
                //...
            }        
        }             
    }   
});

````


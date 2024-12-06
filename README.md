# H3C icons for PlantUML

It uses the topology icons available at [h3c-icon-library](https://github.com/wenyuan/jtopo_topology/blob/master/topo-icons/h3c/h3c-icon-library.ppt).

I saved the file as ``.pptx`` using PowerPoint, renamed it to ``.zip`` and converted the ``*.png`` files on ``media/`` folder to PUML.

PlantUML doesn't handle PNG alpha (transparent images), so I moved the original PNG files to the ``alpha/`` subfolder for anyone interested on them.

Also the PNG rendering was huge, so I resize their width/height by 50%.

Sadly the original file name hasn't been preserved, but you can download this repo and use the "Icon" view on your file manager to see the PNG thumbnails.

The following commands has been run to generate the PlantUML sprites:

```
ls *.png | magick {} -background white -alpha remove -alpha off {}
ls *.png | sed -e 's/\.png$//' | parallel "plantuml -encodesprite 16z {}.png >> {}.puml"
```

## Getting Start

### 802.1X

![802.1X](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/eduardomozart/H3C-PlantUML/master/Samples/Dot1x.puml)

https://github.com/eduardomozart/H3C-PlantUML/blob/59ff55e7ae1c80eed0ba2f0d49e9de93d4bfc13e/Samples/Dot1x.puml#L1-L40

### STP

![STP](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/eduardomozart/H3C-PlantUML/master/Samples/STP.puml)

https://github.com/eduardomozart/H3C-PlantUML/blob/8cec20a438b69c71d91741e2faf5e5dbda739cd9/Samples/STP.puml#L1-L29

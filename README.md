# H3C icons for PlantUML

It uses the topology icons available at [h3c-icon-library](https://github.com/wenyuan/jtopo_topology/blob/master/topo-icons/h3c/h3c-icon-library.ppt).

I saved the file as ``.pptx`` using PowerPoint, renamed it to ``.zip`` and converted the ``*.png`` files on ``media/`` folder to PUML. 

Sadly the original file name hasn't been preserved, but you can download this repo and use the "Icon" view on your file manager to see the PNG thumbnails.

The following command has been run to generate the PlantUML sprites:

```
ls *.png | sed -e 's/\.png$//' | parallel "plantuml -encodesprite 16z {}.png >> {}.puml"
```

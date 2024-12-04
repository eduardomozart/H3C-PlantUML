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

## Sample

![Sample](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/eduardomozart/H3C-PlantUML/master/Sample.iuml)

```csharp
@startuml
skinparam linetype ortho
skinparam nodesep 200
skinparam style strictuml

!define H3CPuml https://raw.githubusercontent.com/eduardomozart/H3C-PlantUML/main/puml
!include H3CPuml/image39.puml
!include H3CPuml/image356.puml
!include H3CPuml/image365.puml

<style>
element {
  FontColor transparent
  LineColor transparent
  BackgroundColor transparent
}
</style>

class "<color:#black><b>Suplicante" as Supplicant {
    \n<U+0020><color:#172D6F><$image365{scale=0.60}></color>
    {method} \n\n
}

class "<color:#black><b>Autenticador" as Authenticator {
    \n<U+0020><U+0020><color:#172D6F><$image39{scale=0.75}></color>
    {method} <color:#black><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><size:11>Switch\n<color:#black><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><size:11>AP\n<color:#black><U+0020><U+0020><U+0020><size:11> Controladora
}

class "<color:#black><b>Servidor RADIUS</color>\n<color:#black><b>AD DS</color>" as Server {
    <U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><U+0020><color:#172D6F><$image356{scale=0.75}></color>\n\n
}

Supplicant -[#black]> Authenticator : <color:#black>Layer 2
Supplicant -[#black]> Authenticator : <U+0020>
Supplicant -[#black]> Authenticator : <color:#black>EAPoL - EAPoW

Authenticator -[#black]> Server : <color:#black>Layer 3
Authenticator -[#black]> Server : <U+0020>
Authenticator -[#black]> Server : <color:#black>RADIUS
@enduml
```

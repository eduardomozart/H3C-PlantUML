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

![Basic Usage - DHCP](https://www.plantuml.com/plantuml/png/ZLDXJzim4FtkNt7GVTYqqT2cBHAg8bWhX3JM8HYV61zCV4qj75zcNxOnjFy-9sbHmeWqjKhaT-_UUtTkJpnBnsLkX7_Gjf1Evk2aVV1OmD6q1LfIM86ZDcYqHNui4CZnXeJ1DGCJE9rj69HscB8cApPQ8UGOACgtkZq_6WnFfzCN2PQubgNXh_YBJutER8wM8GqFT4BiALm7NpYF5vUX3JRCXJ-E8YT_3ZFDc_A-zEXI2cpBmvJo25KfdQASVal7KUWxk3JIyitdYoYNseezRLDJgcV9IESomtWs7HRXr5UUpfgocDU3908Dra6V1C1Pi5-G8GVifFLXh509-4L8_Xh-KQOFcQFIgd-hVuIeDYbjPX2UEYA3E3wQBfPRxBfUw3YSbbfcPALPaBFeO18qvb4JiossloRQ3vAfaTx3DReVw6e7WFdD-yF3yM7o_4uhm-F1w6Yyd9qbypUx9IJpg2ubJTkMTc_2G4cbg1KvM9ulBdUyRxRvX4nRumjPC1LRunwZsRHhrCtN_-u6QfnUIsA9mpwwx2frMALFAUnbrxGFqiDgrD_mPRr-oHxtiw_mUucUk_oudt-w-DJbJeHusupreRd0Tp24Ap8e6XGERhU_ahk3AlTgr4OIQ9fsv7c7FHQhSQU_I-vmOx6A_rzv8bQJrvI5j9POiYPR3m63rZy11eFRUpBgheqzXTiBtnEqgipDNm00)

```csharp
@startuml
skinparam ranksep 75
skinparam nodesep 15
skinparam linetype ortho
left to right direction
hide methods
skinparam style strictuml
skinparam DefaultTextAlignment center

!define H3CPuml https://raw.githubusercontent.com/eduardomozart/H3C-PlantUML/main/puml
!include H3CPuml/image365.puml
!include H3CPuml/image356.puml

<style>
element {
  FontColor transparent
  LineColor transparent
  BackgroundColor transparent
}

rectangle {
  LineColor #3375CD
  LineStyle 2
  DiagonalCorner 4
}
</style>

rectangle "foo" {
class Server {
    <U+0020><U+0020><color:#172D6F><$image356></color>
    <color:#black>Servidor DHCP</color>\n\n\n\n
}

class Laptop {
    <color:#172D6F><$image365></color>
    <U+0020><U+0020><U+0020><U+0020><U+0020><color:#black>Laptop</color>\n\n\n\n
}

note "<color:#black>DHCP Discover</color>" as N1
note "<color:#black>DHCP Offer</color>" as N2
note "<color:#black>DHCP Request</color>" as N3
note "<color:#black>DHCP ACK</color>" as N4

(Laptop,Server) . Role
Laptop -[#3375CD]- N1
N1 -[#3375CD]-> Server
Laptop <-[#3375CD]- N2
N2 -[#3375CD]- Server
Laptop -[#3375CD]- N3
N3 -[#3375CD]-> Server
Laptop <-[#3375CD]- N4
N4 -[#3375CD]- Server

annotation Role #transparent ##[bold]transparent {
}

}
@enduml
```
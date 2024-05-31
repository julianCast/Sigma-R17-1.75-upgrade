# Sigma-R17-1.75-upgrade
Guia y recursos para convertir tu Sigma R16/R17 de 2.85 a 1.75 sin flasheo de firmware.

📖 Esta guia está basada en este proyecto https://www.printables.com/model/135803-bcn3d-sigma-upgrade-to-175mm, así que si te parece útil por favor déjales un comentario. Las piezas alojadas en la carpeta stl están sacadas de dicho proyecto.

## Materiales
Yo he optado por versiones de TriangleLab ya que son más económicos pero dejo enlaces para e3d también.
- 2x V6 metal only ([e3d](https://e3d-online.com/products/v6-hotend-metal-only), [trianglelab](https://es.aliexpress.com/item/32844028127.html?spm=a2g0o.productlist.main.1.180auZ0SuZ0S2u&algo_pvid=46930666-101e-46f5-95b9-302a308c64f4&algo_exp_id=46930666-101e-46f5-95b9-302a308c64f4-0&pdp_npi=4%40dis%21EUR%2121.04%2111.49%21%21%2122.24%2112.15%21%40211b6a7a17171546464947789eb0d7%2112000024944685018%21sea%21ES%210%21AB&curPageLogUid=mMfJ1ebWMXaK&utparam-url=scene%3Asearch%7Cquery_from%3A))
- 2x Fan Duct de E3D ([e3d](https://e3d-online.com/products/v6-fan-duct), incluido en V6 version trianglelab)
- 2x Extrusores Titan Extruder:
  - 1x estandar ([e3d](https://e3d-online.com/products/titan-extruder?variant=41261794033723), [trianglelab](https://es.aliexpress.com/item/1005003092239261.html?spm=a2g0o.productlist.main.1.2b7d75a7eTuCvX&algo_pvid=7c46b905-35c5-42f0-b837-be9fe780cd50&algo_exp_id=7c46b905-35c5-42f0-b837-be9fe780cd50-0&pdp_npi=4%40dis%21EUR%2134.28%2131.35%21%21%2136.23%2133.13%21%40211b664d17171548065182147e42fa%2112000024944119915%21sea%21ES%210%21AB&curPageLogUid=IzQ4TZBv4p7v&utparam-url=scene%3Asearch%7Cquery_from%3A))
  - 1x mirrored ([e3d](https://e3d-online.com/products/titan-extruder?variant=31134336254011), [trianglelab](https://es.aliexpress.com/item/32993081695.html?spm=a2g0o.productlist.main.1.4f2blHnNlHnNJ1&algo_pvid=f3d2a785-221f-4455-815d-317f77fb95d1&algo_exp_id=f3d2a785-221f-4455-815d-317f77fb95d1-0&pdp_npi=4%40dis%21EUR%2146.92%2127.60%21%21%2149.59%2129.17%21%40211b612817171547415651374e32bd%2112000025391463305%21sea%21ES%210%21AB&curPageLogUid=3n8aJAwvtJjV&utparam-url=scene%3Asearch%7Cquery_from%3A))
- 2m Tubo Bowden Capricorn ([Amazon](https://www.amazon.es/dp/B089KMHC7S/ref=twister_B08PNM4J8T?_encoding=UTF8&psc=1))

## Piezas impresión
Imprimir todo lo que esta en carpeta ´stl´, en filamento PETG, con 60% infill, y 4 walls.

## Pasos de montaje
### 1. Extrusor
Comienza con el extrusor izquierdo (principal). Reemplaza el extrusor actual por el nuevo, conservamos el motor de Sigma. La muela de extrusión puede que este atascada, posiblemente tengas que taladrar el tornillo de paso.

⚠️ Dado que los nuevos extrusores sobresalen algo más que anteriores, tenemos que corregir el y-endstop para evitar choque. Para ello buscamos donde está la superficie que activa dicho endstop y le pegamos la pieza `y-endstop-extension.stl`, eso activará el endstop 4cm antes.

### 2. Hotend
No se reemplaza ni thermistor ni cable calentador. Una vez todo colocado deberia quedar casi igual de altura que el anterior (respecto distancia boquilla - endstop).

### 3. Tubo Capricornio
Reemplazar actual tubo 2.85 con 1.75, a excepción del tubo usado bajo filamento para guiarlo, ahi cortamos y metemos el 1.75 dentro del existente, así mantenemos el sistema actual.

## Ajustes de G-Code

### E-steps
Este motor tiene un ratio diferente al anterior asi que debemos re ajustar los pasos, sigue cualquier [tutorial](https://all3dp.com/2/extruder-calibration-calibrate-e-steps/) para ello. Como ejemplo, a mi me dio 422:
```gcode
M92 E422  ; Numero de pasos para el nuevo extrusor.
M500      ; Graba la configuración en la impresora.
```
### Y-axis home offset
Ya que hemos cambiado anteriormente el y-endstop, ahora debemos cambiar los settings de home de la maquina para que no se choque con el frame frontal.
```gcode
M206 Y-40 ; Y-axis home offset a -40 mm.
M500      ; Graba la configuración en la impresora.
```

## Ajustes Cura Slicer
WIP


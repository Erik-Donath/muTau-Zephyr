# muTau-Zephyr
Compatible Zephyr config for the muTau-RV32-SoC

# Aktueller Research Stand
Bezug auf **Zephyr**:

Ich habe herausgefunden, dass **LiteX** die Datei  
`litex_json2dts_zephyr.py`  
bereitstellt, welche automatisch mit der generierten `csr.csv` die benötigten **Device Tree Overlays** und **Konfigurationsdateien** erzeugt.

### Generierung der Overlay-Dateien
Mit folgendem Befehl lassen sich die Dateien erstellen:

``` bash
/opt/litex/litex/tools/litex_json2dts_zephyr.py --dts overlay.dts --config overlay.config csr.json
```

### Kompilierung eines Zephyr-Beispiels
Wenn **Zephyr** korrekt installiert ist, kann man anschließend ein einfaches *Hello World*-Beispiel für das LiteX-VexRiscv-Board bauen:

```bash
cat overlay.config | xargs west build -b litex_vexriscv samples/hello_world -- -DDTC_OVERLAY_FILE=overlay.dts
```

### Hilfreiche Ressourcen
- **Docker-Setup für Zephyr**:  
  Repository: [https://github.com/ShawnHymel/introduction-to-zephyr](https://github.com/ShawnHymel/introduction-to-zephyr)  
  → Dieses Repo enthält einen vorkonfigurierten **Docker-Container**, der den Einstieg stark vereinfacht.

- **Offizielle Zephyr-Dokumentation**:  
  Weitere Schritte und Konfigurationsdetails sollten anhand der offiziellen Zephyr-Dokumentation nachvollzogen werden.

- **Video-Tutorial-Reihe zu Zephyr**:  
  YouTube-Playlist: [https://www.youtube.com/watch?v=mTJ_vKlMS_4](https://www.youtube.com/watch?v=mTJ_vKlMS_4)

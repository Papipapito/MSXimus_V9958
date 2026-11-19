# 09. Changelog

El MSXimus 60K V9958 es el MSXimus 60K con el VDP V9958 clásico (linaje OCM / ESE, `fpga/tn_vdp_v3_v9958`). Hereda el core v3.8 de la Console 60K, y lo que sigue es qué trae esa base y en qué estado está esta línea.

## Estado de esta línea

- **Sin probar en placa.** El core de esta línea es nuevo y todavía no se ha grabado en una Console 60K.
- **Dos arreglos propios del camino V9958**, que se había quedado atrás respecto al resto del core:
  - El `/WAIT` del Z80 colgaba de una red que ya no conduce nadie. Ahora está atado a 1.
  - El panel F12 (`iosys_bl616`) y su superposición sobre el HDMI solo existían en el otro puente de vídeo. Se han traído al puente `msx2hdmi.sv` del V9958.
- **Sin la DDR3 del SOM**: la VRAM del V9958 y las ondas del OPL4 viven en la SDRAM del dock. La DDR3 queda en reposo y su controlador fuera del build.

## Qué trae (la base v3.8 del 60K)

Todo lo siguiente se validó en placa en la línea del 60K de la que sale esta (la v3.8.4 el 16 de octubre de 2026, la v3.8.0b3 el 2 de octubre y la v3.7.6 el 30 de septiembre), con el VDP de aquella línea; el VDP de esta no.

- **v3.1**: el core reconstruido sin el SSRAM de la GW5AT-60B, que Gowin retiró por un problema de silicio (toda memoria pasó a BSRAM o a registros); panel de estado en **F12** por el BL616; identificación como turbo R; ratón MSX desde un ratón USB con cable; el turbo pasa a **F11**.
- **v3.2**: una sola BIOS (el navegador de la SD es el ajuste *Menú al arrancar*); descargas desde el menú con WiFi (tecla F); logo animado en la pantalla del C6.
- **v3.5 a v3.6**: la SD arreglada de raíz (token de escritura, reloj de 6,75 MHz, CRC de lectura); megaram de 4 MB con los mappers NEO-8 y NEO-16; Game Master 2 en el slot 1; guardado de SRAM de cartucho en la tarjeta; Nextor 3 beta.
- **v3.7**: mezclador de audio por chip en Ajustes; SD por DMA (~640 KB/s); mandos HID genéricos por los dos USB-A.
- **v3.7.1 a v3.7.6**: mappers de la Zynq (megaram de 8 MB con ASCII16-X y Plain 0000h); el navegador de la SD ordenado; mandos USB con Report ID; la izquierda fantasma del mando arreglada; el mux de lectura de la CPU en árbol; packs en inglés; el tercer dígito de la versión; MSX SD Maker.
- **v3.8** (core y pack nuevos): actualizar desde el propio MSX (puente de la flash en el dispositivo 4Dh, `MXUPDATE.COM`, ficheros `.UPD`, Ajustes → *Instalar actualización*); el panel F12 en color; el mapper por la firma de la propia ROM (convención de MSXgl); el firmware del C6 con autoridades de certificación.
- **v3.8.1 a v3.8.4**: el OPL4 como el chip real (relectura de los registros, F8 y NEW2, margen del motor wave, fundidos, envolvente, pan, DAMP y pseudo-reverb, el ruido de *Dutch Moonsound Veterans*).

Los detalles de cada entrega (dados de síntesis, márgenes de temporización y hashes) viven en el repositorio privado del mantenedor.

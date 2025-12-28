# IDS – Snort y Suricata

## Resumen
Este repositorio documenta la implementación de un Sistema de Detección de Intrusiones (IDS) en un entorno Linux, utilizando Snort y Suricata. El objetivo del proyecto es definir reglas propias, generar tráfico de prueba controlado para validar las detecciones y analizar los resultados obtenidos a través de logs y evidencias.

El trabajo se ha realizado en el contexto de una práctica académica de ciberseguridad, con un enfoque técnico y formativo.

---

## Entorno de trabajo
- Sistema operativo: Ubuntu (máquina virtual)
- Hostname del sistema: `IDS-GiselaAlascio`
- Herramientas utilizadas:
  - Snort
  - Suricata
  - Nmap
  - Curl
  - Ping
  - hping3

---

## Tramo A – Snort

En este tramo se implementa Snort como IDS principal y se desarrollan **cinco reglas personalizadas**, diseñadas para detectar distintos tipos de tráfico potencialmente sospechoso.

### Tipos de detección implementados
- Escaneo TCP mediante combinación de flags (XMAS scan)
- Detección de patrones en contenido HTTP
- ICMP Echo Request saliente
- Consultas DNS a servidores no autorizados
- Detección de posible ataque DoS (ping flood) mediante `detection_filter`

Las reglas se encuentran en el archivo: `snort/local.rules`

Cada regla ha sido validada mediante tráfico de prueba controlado, comprobando su activación en los logs de Snort.

---

## Tramo B – Suricata

Se implementa Suricata como IDS alternativo y se define una regla personalizada equivalente a una de las reglas desarrolladas en Snort, con el objetivo de comparar ambos motores.

### Comparativa Snort vs Suricata
- **Sintaxis de reglas**: muy similar y altamente compatible
- **Arquitectura**: Snort es tradicionalmente monohilo; Suricata soporta multihilo
- **Formato de logs**: Snort utiliza formatos clásicos; Suricata genera logs estructurados en JSON
- **Escalabilidad**: Suricata resulta más adecuada para entornos de alto tráfico

---

## Conclusiones
El laboratorio demuestra la utilidad de los IDS basados en reglas para la detección de comportamientos anómalos en red. Snort es una herramienta adecuada para entornos educativos y de laboratorio, mientras que Suricata ofrece ventajas claras en rendimiento, análisis y escalabilidad para entornos profesionales.

---

## Contenido del repositorio
- Informe completo en PDF
- Reglas personalizadas de Snort y Suricata
- Capturas de evidencias

---
## Demostración en vídeo

Puedes ver la demostración completa en YouTube:

https://youtu.be/PB6EN9x0ODo

El video muestra:
- Instalación y configuración de Snort y Suricata
- Generación de tráfico de prueba
- Activación de reglas personalizadas
- Verificación de logs y alertas

---

## Nota
Todo el tráfico generado en este proyecto es **controlado y realizado en un entorno de laboratorio**.
No se utilizan sistemas productivos ni datos reales.

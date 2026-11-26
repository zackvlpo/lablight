[README.txt](https://github.com/user-attachments/files/35440494/README.txt)
================================================================================
LABLIGHT VIRTUAL - SIMULADOR DE ESPECTROFOTOMETRIA Y LEY DE BEER-LAMBERT
================================================================================

Proyecto: LabLight Virtual
Asignatura: Proyecto de Innovacion Tecnologica (Universidad Mayor)
Sitio web del simulador: https://zackvlpo.github.io/lablight/
Repositorio: https://github.com/zackvlpo/lablight

1. DESCRIPCION GENERAL
--------------------------------------------------------------------------------
LabLight Virtual es una aplicacion web interactiva para simular ensayos de
espectrofotometria de absorcion y analizar la Ley de Beer-Lambert en tiempo real
desde cualquier navegador (computador, tablet o telefono), sin necesidad de
instalar programas ni usar equipos fisicos de laboratorio.

El programa combina:
- Un panel de configuracion experimental (longitud de onda, paso optico,
  concentracion y ruido gaussiano).
- Un banco optico animado con emisor LED, lente, cubeta dinamica y sensor.
- Graficos interactivos con Chart.js (Transmitancia vs. Concentracion y
  Absorbancia vs. Concentracion) mas ajuste lineal (pendiente y R2).
- Una tabla de registro de datos y exportador a archivo CSV compatible con Excel.
- Acceso directo en la cabecera a la Guia del Estudiante y la Guia del Docente.

2. ESTRUCTURA DEL REPOSITORIO
--------------------------------------------------------------------------------
lablight/
|-- index.html
|-- README.md
`-- guias/
    |-- Guia_Estudiante_LabLight.pdf
    `-- Guia_Docente_LabLight.pdf

3. MODELO MATEMATICO Y PARAMETROS
--------------------------------------------------------------------------------
Variables configurables en el simulador:
- Concentracion (c): de 0.00 M a 1.00 M (pasos de 0.05 M).
- Paso optico (L): 0.5 cm, 1.0 cm o 2.0 cm (ajusta el ancho visual de la cubeta).
- Longitud de onda (lambda):
  * 470 nm (Azul):   epsilon = 1.8 L/(mol*cm)
  * 525 nm (Verde):  epsilon = 2.5 L/(mol*cm)
  * 630 nm (Rojo):   epsilon = 3.2 L/(mol*cm)
- Ruido gaussiano (delta): interruptor ON/OFF con variacion aproximada de +/-1.5%
  (rango de referencia entre +/-0.5% y +/-2.0%).

Ecuaciones utilizadas:
- Transmitancia: T = I / I0 = 10^(-epsilon * c * L)
- Absorbancia:   A = -log10(T) = epsilon * c * L
- Intensidad simulada con ruido: I_simulada = I0 * 10^(-epsilon * c * L) + delta

4. FLUJO DE USO EN EL SIMULADOR
--------------------------------------------------------------------------------
1. Ajustar concentracion en c = 0.00 M y pulsar "Calibrar Blanco (I0)" para
   fijar I0 = 100.0% y A = 0.000 AU.
2. Elegir longitud de onda (lambda), paso optico (L) y si se desea activar el
   ruido gaussiano.
3. Mover el control de concentracion (c) y pulsar "Registrar Muestra (I)" para
   guardar cada lectura en la tabla y actualizar los graficos y la regresion.
4. Usar "Guardar Serie p/ Comparar" para conservar una serie y superponer otra
   variando parametros o el ruido.
5. Pulsar "Exportar Datos (.CSV / Excel)" para descargar los registros en formato
   CSV con codificacion UTF-8 BOM y separador punto y coma (;).
6. Descargar los PDFs desde los botones superiores ("Guia Estudiante (.PDF)" y
   "Guia Docente (.PDF)").

5. LIMITACIONES CONOCIDAS
--------------------------------------------------------------------------------
- Trabaja con tres longitudes de onda discretas (470, 525 y 630 nm) y no
  realiza barrido espectral continuo.
- El ruido es simulado estadisticamente y no reproduce efectos fisicos reales
  como luz parasita, reflexiones en celdas o desviaciones quimicas extremas.
- Los datos se mantienen en memoria durante la sesion del navegador hasta que
  se reinicia el ensayo o se exportan a CSV.
























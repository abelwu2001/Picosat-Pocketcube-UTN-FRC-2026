# PocketQube PoCat: análisis, ensayos y propuestas de mejora

Este repositorio reúne la documentación, los diseños electrónicos y los resultados del estudio del satélite **PocketQube PoCat**. El trabajo parte de un diseño existente y busca identificar mejoras comprobables mediante simulaciones, mediciones y comparaciones con la versión original.

La configuración principal analizada utiliza el **payload PL2**, destinado a la detección de interferencias de radiofrecuencia en banda L.

> [!IMPORTANT]
> Antes de modificar una placa, hay que confirmar su revisión, función, compatibilidad mecánica y relación con las demás placas del satélite. Todos los cambios deben realizarse sobre una copia del diseño original.

## Objetivos del proyecto

- Comprender el funcionamiento completo del PocketQube.
- Identificar la función y las conexiones de cada placa.
- Reunir los resultados obtenidos por los desarrolladores del diseño original.
- Detectar limitaciones reales mediante mediciones o simulaciones.
- Seleccionar una mejora técnicamente justificable.
- Comparar el comportamiento del diseño original con el modificado.
- Documentar el procedimiento y los resultados para que puedan reproducirse.

## Configuración del satélite

### Placas y elementos principales

| Carpeta o placa | Función principal | Uso en la configuración PL2 |
|---|---|---|
| `pq_obc_comms` | Computadora de a bordo y comunicación LoRa | Se utiliza |
| `pq_eps` | Gestión de energía, MPPT, batería y distribución de tensiones | Se utiliza |
| `pq_adcs` | Determinación y control de actitud | Se utiliza |
| `pq_ymag_board` | Magnetorquer del eje Y | Se utiliza |
| `pq_latboard` | Placas laterales con panel solar y sensores; una incorpora la antena | Se utilizan varias unidades |
| `pq_botboard` | Placa inferior, panel solar, batería, umbilical y *killswitches* | Se utiliza |
| `pq_botnotsobot` | Placa inferior deslizante o estructural del conjunto | Se utiliza |
| `pq_pl1` | Payload de cámara VGA | No se utiliza con PL2 |
| `pq_pl2` | Payload de detección RFI en banda L | Payload seleccionado |
| `pq_topboard` | Placa superior genérica | Alternativa al payload, según la configuración |
| `pq_egse` | Equipo eléctrico de apoyo y pruebas en tierra | No vuela |
| `assembly` | Modelos y archivos del ensamblaje mecánico | Solo documentación/diseño |

> [!NOTE]
> **Enlaces generales del proyecto — completar después**
>
> ```text
> Repositorio principal:
> Wiki o documentación oficial:
> Procedimiento de ensamblaje:
> Lista de materiales general:
> Modelos mecánicos:
> ```

## Orden funcional del sistema

El recorrido general de energía, control y datos puede resumirse así:

1. Los paneles solares entregan energía a la `pq_eps`.
2. La EPS administra la carga de la batería y alimenta las demás placas.
3. La `pq_obc_comms` controla el satélite y transmite o recibe información.
4. La `pq_adcs` mide y controla la orientación mediante sensores y magnetorquers.
5. La `pq_pl2` realiza las mediciones de interferencia en banda L.

## Documentación por subsistema

### OBC y comunicaciones

Incluye el microcontrolador, la memoria, la telemetría y el transceptor LoRa. En esta sección se documentarán la potencia transmitida, sensibilidad, frecuencia, adaptación de impedancias, armónicos y alcance del enlace.

> [!NOTE]
> **Enlaces de OBC y comunicaciones — completar después**
>
> ```text
> Esquemático y PCB:
> Documentación del SX1262:
> Red de adaptación RF:
> Antena y despliegue:
> Firmware:
> Resultados de los ensayos:
> ```

### EPS y batería

La EPS recibe la energía de los paneles solares, realiza el seguimiento del punto de máxima potencia, carga la batería y distribuye las tensiones necesarias.

> [!NOTE]
> **Enlaces de energía — completar después**
>
> ```text
> Esquemático y PCB:
> Descripción del MPPT:
> Batería utilizada:
> Paneles solares:
> Protecciones eléctricas:
> Resultados de eficiencia y rizado:
> ```

### ADCS y magnetorquers

El ADCS estima la orientación del satélite mediante sus sensores y acciona los magnetorquers para reducir el giro o modificar la actitud.

> [!NOTE]
> **Enlaces de ADCS — completar después**
>
> ```text
> Esquemático y PCB:
> Sensores utilizados:
> Magnetorquers:
> Algoritmo de control:
> Firmware:
> Resultados de calibración y estabilización:
> ```

### Payload PL2

PL2 es la carga útil seleccionada para estudiar interferencias de radiofrecuencia en banda L. Deben documentarse su banda de trabajo, ganancia, sensibilidad, piso de ruido, linealidad, calibración e inmunidad frente a las emisiones del propio satélite.

> [!NOTE]
> **Enlaces del payload PL2 — completar después**
>
> ```text
> Esquemático y PCB:
> Descripción del radiómetro:
> Componentes principales:
> Procedimiento de calibración:
> Datos o mediciones originales:
> Publicaciones relacionadas:
> ```

## Posibles líneas de mejora

### 1. Mejorar el sistema de energía

- Aumentar la eficiencia de los convertidores.
- Revisar el funcionamiento del MPPT.
- Reducir el rizado de las alimentaciones.
- Mejorar el diseño térmico y las pistas de potencia.
- Disminuir las emisiones de las etapas conmutadas.

### 2. Mejorar el sistema de comunicaciones

- Optimizar la adaptación de la antena a `50 Ω`.
- Revisar la pista RF y su camino de retorno.
- Reducir armónicos del transmisor.
- Mejorar el mecanismo de despliegue.
- Comparar alcance, potencia y sensibilidad.

### 3. Mejorar el control de actitud

- Calibrar magnetómetro, giróscopo y sensores solares.
- Filtrar ruido y deriva de los sensores.
- Mejorar el algoritmo de estimación y control.
- Optimizar el accionamiento de los magnetorquers.
- Evitar que las bobinas interfieran con el magnetómetro.

### 4. Reducir interferencias electromagnéticas

- Medir el piso de ruido de PL2 en forma aislada.
- Encender cada subsistema por separado para identificar la fuente de ruido.
- Revisar planos de masa y caminos de retorno.
- Agregar filtros, ferritas, desacoplos o blindaje cuando corresponda.
- Evaluar una ventana silenciosa de medición mediante firmware.
- Comparar los espectros antes y después de la modificación.

### 5. Mejorar el payload de cámara

- Aumentar resolución o calidad de imagen.
- Reducir el consumo entre capturas.
- Incorporar memoria o compresión.
- Mejorar el protocolo de transferencia.

> [!WARNING]
> La mejora de cámara corresponde principalmente a `pq_pl1`. No debe agregarse PL1 a la configuración PL2 sin comprobar espacio, masa, consumo, conexiones y compatibilidad con el ensamblaje.

## Procedimiento para realizar modificaciones

1. Confirmar la revisión exacta de la placa.
2. Guardar una copia sin modificar en `hardware/original/`.
3. Crear una rama o carpeta para la propuesta.
4. Documentar el problema y el requisito de mejora.
5. Registrar valores y mediciones iniciales.
6. Modificar una sola variable o zona por vez.
7. Ejecutar nuevamente el mismo ensayo.
8. Comparar los resultados en iguales condiciones.
9. Guardar esquemáticos, PCB, BOM, Gerbers y firmware utilizados.
10. Registrar conclusiones, limitaciones y trabajos pendientes.

> [!CAUTION]
> No enviar a fabricar una placa modificada sin ejecutar las verificaciones eléctricas y de diseño correspondientes. Prestar especial atención a la batería, los convertidores de potencia, la pista RF, los conectores entre placas y las restricciones mecánicas del ensamblaje.

## Estado del proyecto

- [ ] Reunir todos los enlaces oficiales.
- [ ] Confirmar las revisiones de las placas.
- [ ] Conseguir resultados y mediciones originales.
- [ ] Definir requisitos cuantitativos.
- [ ] Seleccionar la mejora definitiva.
- [ ] Realizar simulaciones y ensayos iniciales.
- [ ] Implementar la modificación.
- [ ] Comparar resultados.
- [ ] Preparar documentación final.

## Integrantes

```text
Institución:
Carrera:
Materia o proyecto:
Integrantes:
Docentes:
Año:
```

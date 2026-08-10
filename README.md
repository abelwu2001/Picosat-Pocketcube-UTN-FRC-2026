# PocketQube PoCat: análisis, ensayos y propuestas de mejora

Este repositorio reúne la documentación, los diseños electrónicos y los resultados del estudio del satélite **PocketQube PoCat**. El trabajo parte de un diseño existente y busca identificar mejoras comprobables mediante simulaciones, mediciones y comparaciones con la versión original.

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


## Orden funcional del sistema

El recorrido general de energía, control y datos puede resumirse así:

1. Los paneles solares entregan energía a la `pq_eps`.
2. La EPS administra la carga de la batería y alimenta las demás placas.
3. La `pq_obc_comms` controla el satélite y transmite o recibe información.
4. La `pq_adcs` mide y controla la orientación mediante sensores y magnetorquers.
5. La `pq_pl2` realiza las mediciones de interferencia en banda L.


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

## Integrantes

```text
Institución:
Carrera:
Materia o proyecto:
Integrantes:
Docentes:
Año:
```

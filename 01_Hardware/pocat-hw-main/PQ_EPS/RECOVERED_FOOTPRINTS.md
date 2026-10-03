# Huellas recuperadas del PCB

Recovered_Project.pretty contiene una copia editable por instancia de las huellas embebidas en este PCB, exportada con KiCad. Los nombres incluyen referencia y UUID abreviado para conservar variantes y modificaciones locales. recovered-footprints.json registra el identificador original, el nuevo y los hashes.

Esta biblioteca es una instantánea del diseño existente; no representa validación del fabricante ni del repositorio NSL. Conserva también cualquier defecto pendiente de pads, courtyards o geometría. Las reglas DRC permanecen activas y los cambios futuros respecto de esta instantánea vuelven a producir avisos de discrepancia.

La operación cambia únicamente los identificadores de biblioteca del PCB y la propiedad Footprint de los símbolos colocados correspondientes. Se verifica que la serialización nativa del PCB sea idéntica salvo esos identificadores; no se sustituyen pads ni se modifican redes. Los modelos 3D conservan sus rutas originales y pueden requerir dependencias externas.

Para comparar con la fuente histórica, consultar original_fpid y sources/nanosatlab. No ejecutar Actualizar huellas desde bibliotecas de forma masiva con las bibliotecas actuales ajenas a esta instantánea sin revisar diferencias.

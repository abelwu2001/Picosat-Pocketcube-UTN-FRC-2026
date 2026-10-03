# Símbolos recuperados del esquemático

Recovered_Symbols contiene las definiciones embebidas del proyecto. sym-lib-table conserva sus nicknames originales y apunta a estas copias locales. El esquemático y sus lib_id, pines, tipos eléctricos, cables, redes y reglas ERC permanecen intactos.

Son instantáneas del diseño histórico, no bibliotecas validadas por el fabricante. Los defectos y las variantes locales se conservan. recovered-symbols.json registra los bloques de origen mediante hashes y cualquier traducción estructural de nombre. Embedded_Local_Variants conserva exactamente los símbolos locales lib_name; si falta una definición canónica, se deriva de una de esas variantes renombrando únicamente los nombres estructurales de símbolo.

No se añadieron PWR_FLAG, exclusiones ni cambios de severidad para eliminar errores eléctricos. Los avisos de diferencia reales entre variantes locales y su definición canónica deben revisarse expresamente.

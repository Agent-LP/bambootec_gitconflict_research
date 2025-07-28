# Solución: Imágenes no se muestran en el reporte de Power BI tras rebase

## Problema
Al realizar un rebase, puede que las imágenes no se muestren en el reporte de Power BI. Esto ocurre por conflictos en el archivo `report.json` ubicado en la carpeta del reporte y luego en la subcarpeta `definition`.

## Solución

1. **Resolver conflictos en `report.json`:**
   - Abre el archivo `bambootec_gitconflict_research.Report/definition/report.json`.
   - Busca la propiedad `resourcePackages`, que es una lista de objetos.

2. **Verificar el objeto `RegisteredResources`:**
   - Dentro de `resourcePackages`, localiza el objeto con `"name": "RegisteredResources"`.
   - En la propiedad `items` de este objeto, asegúrate de que estén listadas todas las imágenes que necesitas mostrar en el reporte.
   - Cada imagen debe tener una entrada similar a:
     ```json
     {
       "name": "nombre_de_la_imagen.jpg",
       "path": "nombre_de_la_imagen.jpg",
       "type": "Image"
     }
     ```

3. **Guardar los cambios:**
   - Una vez verificado y corregido el listado de imágenes, guarda el archivo.

4. **Verifica en Power BI:**
   - Abre el reporte en Power BI y comprueba que las imágenes se muestran correctamente.

## Notas
- Si hay conflictos de git, resuélvelos manualmente asegurando que no se pierdan referencias a imágenes necesarias.
- Repite el proceso en cada archivo `report.json` relevante si tienes más de uno en el proyecto.
- Verifica siempre que los nombres de las imágenes coincidan en todos los lugares donde se referencian:
   * En la carpeta [visuals](https://github.com/Agent-LP/bambootec_gitconflict_research/tree/fix/imageSobreposition/bambootec_gitconflict_research.Report/definition/pages/c9aa5df950a2d49925a9/visuals)
   * En la carpeta [RegisteredResources](https://github.com/Agent-LP/bambootec_gitconflict_research/tree/fix/imageSobreposition/bambootec_gitconflict_research.Report/StaticResources/RegisteredResources)
   * En el archivo [report.json](https://github.com/Agent-LP/bambootec_gitconflict_research/blob/fix/imageSobreposition/bambootec_gitconflict_research.Report/definition/report.json)
- Para mayor seguimiento de las imagenes puedes cambiarle el nombre de carpeta a cada visual para saber de que visual se trata
---

Con estos pasos, las imágenes deberían aparecer correctamente en el reporte tras un rebase.
# Especificación de Feature: Planificador de Menús Familiares

**Rama**: `001-planificador-menus-familiares`
**Creada**: 2026-07-16
**Estado**: Aprobado
**Input**: Descripción del usuario: "Quiero crear una aplicación que ayudara a planificar los menús familiares teniendo en cuenta distintos criterios, necesidades nutricionales, preferencias alimentarias, restricciones. Objetivos perder peso, ganar masa muscular, etcétera. Incluso que generas automáticamente la lista de la compra a partir del menú semana."

---

## Escenarios de usuario y pruebas *(obligatorio)*

### Historia de Usuario 1 - Dar de alta recetas (Prioridad: P1)

Como usuario de la aplicación, quiero dar de alta nuevas recetas especificando el nombre, los ingredientes con sus cantidades, el tipo de comida y el aporte nutricional, para tener un catálogo de platos disponible para planificar mi menú semanal.

**Por qué esta prioridad**: sin recetas dadas de alta, no hay material con lo que planificar. Es la base sobre la que se construye todo lo demás.

**Test independiente**: se puede probar creando una receta completa con ingredientes y verificando que queda guardada y visible en el listado, sin necesitar planificación ni búsqueda.

**Escenarios de aceptación**:
1. **Dado** que soy un usuario registrado, **Cuando** creo una nueva receta con nombre, ingredientes con cantidades, tipo de comida y aporte nutricional, **Entonces** la receta queda guardada y aparece en mi listado de recetas.
2. **Dado** que soy un usuario registrado, **Cuando** intento guardar una receta sin nombre o sin al menos un ingrediente, **Entonces** el sistema me muestra un error indicando los campos obligatorios faltantes.
3. **Dado** que tengo una receta ya dada de alta, **Cuando** edito los ingredientes o el aporte nutricional y guardo los cambios, **Entonces** la receta se actualiza con los nuevos datos.

### Historia de Usuario 2 - Buscar recetas por nombre o ingrediente (Prioridad: P1)

Como usuario que tiene muchas recetas dadas de alta, quiero buscar recetas por el nombre del plato o por algún ingrediente en concreto, para encontrar rápidamente lo que quiero incluir en mi menú.

**Por qué esta prioridad**: a medida que crece el catálogo de recetas, la búsqueda es imprescindible para localizar platos sin tener que recorrer toda la lista.

**Test independiente**: se puede probar añadiendo el término de búsqueda y verificando que los resultados filtrados son correctos, sin necesitar planificación.

**Escenarios de aceptación**:
1. **Dado** que tengo varias recetas dadas de alta, **Cuando** busco por el nombre de un plato, **Entonces** aparecen las recetas cuyo nombre contiene el término de búsqueda.
2. **Dado** que tengo varias recetas con distintos ingredientes, **Cuando** busco por un ingrediente, **Entonces** aparecen todas las recetas que contienen ese ingrediente.
3. **Dado** que hago una búsqueda, **Cuando** el término no coincide con ninguna receta, **Entonces** el sistema me indica que no se encontraron resultados.

### Historia de Usuario 3 - Ver listado de recetas organizado por tipo de comida (Prioridad: P1)

Como usuario, quiero ver el listado de mis recetas organizadas por tipo de comida (desayuno, aperitivos, entrantes, comidas o cenas), para navegar fácilmente por el catálogo y elegir platos según el momento del día.

**Por qué esta prioridad**: la organización por tipo de comida es clave para cuando el usuario va a planificar su menú semanal y necesita seleccionar platos según la comida del día.

**Test independiente**: se puede probar accediendo al listado y verificando que las recetas aparecen agrupadas por categoría, sin necesitar planificación.

**Escenarios de aceptación**:
1. **Dado** que tengo recetas de distintos tipos dadas de alta, **Cuando** accedo al listado de recetas, **Entonces** veo las recetas agrupadas por tipo de comida (desayuno, aperitivos, entrantes, comidas, cenas).
2. **Dado** que no tengo recetas de un tipo de comida en concreto, **Cuando** accedo al listado, **Entonces** esa categoría aparece vacía o no se muestra.

### Historia de Usuario 4 - Planificar menú semanal (Prioridad: P1)

Como usuario, quiero planificar mi menú semanal seleccionando platos del catálogo de recetas para cada día y tipo de comida, para tener organizada la alimentación de la semana.

**Por qué esta prioridad**: es el núcleo de la aplicación. Sin planificación semanal, la app no cumple su propósito principal.

**Test independiente**: se puede probar seleccionando recetas para los días de la semana y verificando que la planificación se guarda y visualiza correctamente.

**Escenarios de aceptación**:
1. **Dado** que tengo recetas dadas de alta, **Cuando** asigno una receta a un día y tipo de comida concreto de la semana, **Entonces** la planificación se guarda y muestra la receta asignada en ese día.
2. **Dado** que estoy planificando, **Cuando** selecciono una receta cuyo tipo de comida no coincide con el slot que estoy rellenando (por ejemplo, una receta de "cena" en el slot de "desayuno"), **Entonces** el sistema permite la asignación cruzada sin restricción.
3. **Dado** que intento planificar sin tener recetas dadas de alta, **Cuando** accedo a la planificación semanal, **Entonces** el sistema me indica que necesito dar de alta recetas primero.

### Historia de Usuario 5 - Planificación flexible con días libres o comidas fuera (Prioridad: P2)

Como usuario, quiero poder dejar días sin planificar o marcar que un día he comido fuera de casa, para que la planificación se adapte a mi vida real y no sea rígida.

**Por qué esta prioridad**: aporta flexibilidad y usabilidad real, pero depende de que la planificación base (P1) ya exista.

**Test independiente**: se puede probar marcando un día como "comido fuera" o dejándolo vacío y verificando que la planificación se acepta sin errores.

**Escenarios de aceptación**:
1. **Dado** que estoy planificando la semana, **Cuando** marco un día como "comido fuera de casa", **Entonces** ese día aparece marcado con esa indicación y no obliga a seleccionar receta.
2. **Dado** que estoy planificando la semana, **Cuando** dejo un día sin asignar receta ni marcar como comida fuera, **Entonces** ese día queda como día libre sin planificar sin generar error.
3. **Dado** que marqué un día como "comido fuera", **Cuando** quiero cambiarlo y asignar una receta, **Entonces** puedo seleccionar una receta y sustituir la marca de "comido fuera".

### Historia de Usuario 6 - Aviso al repetir plato en la semana (Prioridad: P2)

Como usuario que planifica su menú semanal, quiero que el sistema me avise si asigno el mismo plato a más de un día de la semana, para ser consciente de la repetición y decidir si la acepto o busco variedad.

**Por qué esta prioridad**: mejora la calidad de la planificación y aporta variedad, pero no es imprescindible para que la funcionalidad base funcione.

**Test independiente**: se puede probar asignando el mismo plato dos veces en la semana y verificando que aparece el aviso.

**Escenarios de aceptación**:
1. **Dado** que ya he asignado un plato a un día de la semana, **Cuando** asigno el mismo plato a otro día, **Entonces** el sistema me muestra un aviso indicando que el plato ya está repetido y me pregunta si confirmo la repetición.
2. **Dado** que recibí un aviso de repetición, **Cuando** confirmo que quiero repetir el plato, **Entonces** la asignación se guarda correctamente.
3. **Dado** que recibí un aviso de repetición, **Cuando** decido no repetir el plato, **Entonces** la asignación no se guarda y puedo elegir otro plato.

### Historia de Usuario 7 - Consultar valores nutricionales desde la API (Prioridad: P2)

Como usuario que da de alta una receta, quiero consultar los valores nutricionales de un ingrediente desde una fuente externa, para no tener que introducirlos manualmente y asegurar que los datos son fiables.

**Por qué esta prioridad**: simplifica el alta de recetas y mejora la calidad de los datos nutricionales, pero no es imprescindible para que la funcionalidad base funcione (el usuario puede introducir los datos manualmente).

**Test independiente**: se puede probar consultando un alimento concreto y verificando que se devuelven los valores nutricionales correctos, sin necesitar recetas ni planificación.

**Escenarios de aceptación**:
1. **Dado** que estoy dando de alta una receta y relleno un ingrediente, **Cuando** consulto los valores nutricionales de ese ingrediente mediante la API, **Entonces** el sistema muestra las calorías, carbohidratos, grasas y proteínas del alimento.
2. **Dado** que consulto un ingrediente, **Cuando** la API devuelve resultados, **Entonces** puedo seleccionar el alimento correcto y los valores nutricionales se aplican al ingrediente de la receta.
3. **Dado** que intento consultar un ingrediente, **Cuando** la API no encuentra resultados para ese alimento, **Entonces** el sistema me indica que no se encontraron datos nutricionales y me permite introducir los valores manualmente.
4. **Dado** que intento consultar un ingrediente, **Cuando** la API no está disponible o tarda en responder, **Entonces** el sistema muestra un aviso de error y me permite introducir los valores manualmente.

### Historia de Usuario 8 - Notificación de cambios en receta planificada (Prioridad: P2)

Como usuario que tiene una receta planificada en mi menú semanal, quiero ser notificado cuando esa receta se ha modificado (ingredientes o aporte nutricional), para decidir si quiero aplicar los cambios a mi planificación o mantener la versión anterior.

**Por qué esta prioridad**: permite editar recetas en uso sin romper las planificaciones existentes, pero depende de que la edición de recetas (P1) y la planificación (P1) ya existan.

**Test independiente**: se puede probar modificando una receta que está en una planificación activa y verificando que el usuario recibe la notificación con la opción de actualizar o mantener.

**Escenarios de aceptación**:
1. **Dado** que tengo una receta planificada en mi menú semanal, **Cuando** edito esa receta (ingredientes o aporte nutricional), **Entonces** el sistema me notifica que la receta tiene cambios pendientes y me pregunta si quiero aplicarlos a la planificación.
2. **Dado** que recibí una notificación de cambios en una receta planificada, **Cuando** decido aplicar los cambios, **Entonces** la planificación se actualiza con la nueva versión de la receta.
3. **Dado** que recibí una notificación de cambios en una receta planificada, **Cuando** decido mantener la versión actual, **Entonces** la planificación conserva la versión anterior de la receta sin cambios.

### Casos límite

- ¿Qué pasa si un usuario intenta eliminar una receta que ya está asignada en un menú semanal planificado? El sistema NO debe permitir la eliminación y debe mostrar un aviso.
- ¿Cómo se comporta el sistema si un usuario intenta planificar una semana sin tener recetas de algún tipo de comida? El sistema permite planificar con slots vacíos.
- ¿Qué pasa si un usuario edita los ingredientes de una receta que está siendo usada en una planificación activa? El sistema permite la edición y notifica al usuario con la opción de aplicar los cambios o mantener la versión anterior en la planificación.
- ¿Qué pasa si un usuario elimina su cuenta? Se eliminan todas sus recetas y planificaciones asociadas, ya que los datos son exclusivos de cada usuario.
- ¿Qué pasa si la API Food Data Central no está disponible? El sistema debe permitir la introducción manual de valores nutricionales como fallback.
- ¿Cómo se maneja el límite de semanas cuando el usuario intenta planificar una 5ª semana? El sistema muestra un aviso indicando que se ha alcanzado el límite de 4 semanas a futuro y no permite planificar más allá.

---

## Requisitos *(obligatorio)*

### Requisitos funcionales

- **FR-001**: El sistema DEBE permitir a un usuario registrado dar de alta una nueva receta especificando nombre, ingredientes con cantidades, tipo de comida y aporte nutricional.
- **FR-002**: El sistema DEBE validar que una receta tenga al menos nombre y un ingrediente antes de guardarla.
- **FR-003**: El sistema DEBE permitir editar los datos de una receta ya dada de alta.
- **FR-003A**: El sistema DEBE notificar al usuario cuando se edita una receta que está en uso en una planificación activa, ofreciendo la opción de aplicar los cambios a la planificación o mantener la versión anterior.
- **FR-004**: El sistema DEBE permitir eliminar una receta del catálogo, siempre que no esté en uso en una planificación activa; si la receta está en uso, el sistema DEBE impedir la eliminación y mostrar un mensaje indicando que la receta está asociada a una planificación en curso.
- **FR-005**: El sistema DEBE permitir buscar recetas por nombre del plato o por ingrediente contenido.
- **FR-006**: El sistema DEBE mostrar las recetas organizadas por tipo de comida (desayuno, aperitivos, entrantes, comidas, cenas).
- **FR-007**: El sistema DEBE permitir a un usuario planificar su menú semanal asignando recetas a días y tipos de comida, permitiendo asignar una receta a un slot de tipo diferente al de la receta.
- **FR-008**: El sistema DEBE permitir marcar un día de planificación como "comido fuera de casa" o dejarlo sin planificar.
- **FR-009**: El sistema DEBE avisar al usuario cuando asigna el mismo plato a más de un día en la misma semana.
- **FR-010**: El sistema DEBE permitir que cada usuario tenga su propio catálogo de recetas y sus propias planificaciones, independientes de otros usuarios.
- **FR-011**: El sistema DEBE permitir el registro e inicio de sesión de usuarios.
- **FR-012**: El sistema DEBE permitir consultar los valores nutricionales de un alimento mediante la integración con la API Food Data Central (FDA) para obtener calorías, carbohidratos, grasas y proteínas.
- **FR-013**: El sistema DEBE permitir al usuario enriquecer una receta consultando los valores nutricionales de sus ingredientes a través de la API Food Data Central y aplicarlos automáticamente al aporte nutricional de la receta.
- **FR-014**: El sistema DEBE almacenar el aporte nutricional de cada receta con los campos: calorías, carbohidratos, grasas y proteínas.

### Entidades clave

- **Usuario**: representa a una persona que usa la aplicación; tiene su propio catálogo de recetas y planificaciones.
- **Receta**: representa un plato de cocina; contiene nombre, lista de ingredientes con cantidades, tipo de comida (desayuno, aperitivos, entrantes, comidas, cenas), y aporte nutricional.
- **Ingrediente**: componente de una receta; tiene nombre y cantidad.
- **Planificación semanal**: colección de asignaciones de recetas a días y tipos de comida para una semana concreta; pertenece a un usuario. El sistema almacena hasta 4 semanas de planificación.
- **Asignación de menú**: relación entre un día de la semana, un tipo de comida y una receta (o estado "comido fuera" / día libre). Si la receta se modifica después de ser asignada, la asignación puede conservar una versión snapshot de la receta anterior o actualizarse a la nueva versión según la decisión del usuario.
- **Aporte nutricional**: información asociada a una receta que incluye los campos: calorías, carbohidratos, grasas y proteínas. Puede introducirse manualmente o consultarse mediante la API Food Data Central.

---

## Criterios de éxito *(obligatorio)*

### Resultados medibles

- **SC-001**: Un usuario puede dar de alta una receta completa en menos de 2 minutos.
- **SC-002**: Un usuario puede planificar un menú semanal completo en menos de 10 minutos.
- **SC-003**: Al menos el 80% de las búsquedas de recetas devuelven resultados relevantes.
- **SC-004**: El sistema permite planificar menús para hasta 4 semanas futuras.
- **SC-005**: La consulta de valores nutricionales mediante la API Food Data Central devuelve resultados en menos de 5 segundos.

---

## Suposiciones

- Los usuarios están registrados e identificados; no hay acceso como usuario anónimo.
- Cada usuario tiene su propio catálogo de recetas y sus propias planificaciones, sin compartir con otros usuarios.
- Queda **FUERA de alcance** en esta versión: generación automática de lista de la compra, filtros por valor nutricional en la planificación, objetivos nutricionales (perder peso, ganar masa muscular), restricciones alimentarias y preferencias dietéticas.
- El tipo de comida de una receta es fijo y se define al darla de alta (desayuno, aperitivos, entrantes, comidas, cenas), pero se permite asignar una receta a un slot de tipo diferente durante la planificación.
- La planificación se organiza por semana y cada día tiene slots para los distintos tipos de comida. El sistema almacena hasta 4 semanas de planificación.
- El sistema integra la API Food Data Central (FDA) para consultar los valores nutricionales de los ingredientes (calorías, carbohidratos, grasas, proteínas). Si la API no está disponible, el sistema permite la introducción manual como fallback.
- La API Food Data Central está disponible y accesible; su documentación se encuentra en: `https://app.swaggerhub.com/apis/fdcnal/food-data_central_api/1.0.1#`.

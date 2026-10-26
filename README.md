# Documentación UML – Guardianes del medio ambiente

**Guardianes del medio ambiente** es un juego educativo en el que un niño o niña recorre habitaciones, detecta problemas de contaminación (luces encendidas sin necesidad, basura tirada, llaves de agua abiertas) y los corrige para convertirse en guardián del medio ambiente. Si el jugador interactúa con algo que no era un problema, puede reiniciar el nivel. Al terminar todos los niveles aparece el mensaje: **"¡Felicidades, eres un guardián del medio ambiente!"**

Esta carpeta contiene el modelado UML del proyecto, realizado con **Mermaid**, que GitHub muestra directamente en el navegador.

## Diagramas

| Diagrama | Archivo |
|----------|---------|
| Casos de uso general | [casos-de-uso.md](casos-de-uso.md) |
| Clases del módulo Niveles y Habitaciones | [diagrama-de-clases.md](diagrama-de-clases.md) |

## Diagrama de casos de uso general

Muestra lo que el **jugador** (único actor) puede hacer en el juego:

- Iniciar el juego y elegir personaje (niño o niña).
- Seleccionar un nivel y explorar la habitación.
- Identificar un problema de contaminación y corregirlo.
- Interactuar con objetos que están correctos.
- Reiniciar el nivel cuando se equivoca.
- Avanzar a la siguiente habitación y ver su progreso.
- Ver el mensaje final de guardián del medio ambiente.

## Diagrama de clases: módulo Niveles y Habitaciones

Este módulo se encarga de organizar el avance del juego a través de niveles, donde cada uno se desarrolla en una habitación.

| Clase | Responsabilidad |
|-------|-----------------|
| **GestorNiveles** | Controla el nivel actual, carga y reinicia niveles, avanza al siguiente y avisa cuando todos están completados. |
| **Nivel** | Representa una etapa del juego. Lleva la cuenta de los problemas que faltan por corregir y se completa cuando llegan a cero. |
| **Habitacion** | Es el escenario del nivel (por ejemplo cocina, baño o sala). Carga y contiene los objetos con los que se interactúa. |
| **ObjetoInteractivo** | Elemento de la habitación. Puede ser un problema (`esProblema = true`) o algo correcto. Su método `interactuar()` indica si la acción del jugador fue acertada. |
| **Problema** | Describe el tipo de contaminación y la solución que el jugador debe aplicar. |

### Relaciones principales

- **GestorNiveles** administra uno o más **Nivel** (agregación).
- Cada **Nivel** se desarrolla en una **Habitacion** (composición).
- Cada **Habitacion** contiene uno o más **ObjetoInteractivo** (composición).
- Un **ObjetoInteractivo** que es problema representa un **Problema**.

### Reglas del juego reflejadas en el modelo

1. Un nivel se completa cuando `problemasRestantes` llega a 0.
2. Si el jugador interactúa con un objeto que no es problema, `GestorNiveles` ejecuta `reiniciarNivel()`.
3. Cuando todos los niveles están completados, el juego muestra el mensaje final.

## Herramienta utilizada

Mermaid (los diagramas se escriben como texto y GitHub los renderiza automáticamente).

## Integrantes del equipo

- José Manuel Ramos Chávez
- (agrega aquí a tus compañeros)

# Arquitecturas de referencia

[English](README.md) · **Español**

Formas que hemos construido más de una vez, con el compromiso escrito en vez de sobreentendido.

Cada una declara qué optimiza, qué cuesta y cuándo **no** usarla. Una nota de arquitectura
sin sección de "cuándo no usar esto" es marketing.

| Patrón | Optimiza | Coste principal |
| --- | --- | --- |
| [Pipeline con la IA al final](ai-last-pipeline.es.md) | Coste por petición; superficie de prompt injection | Una capa de reglas que hay que mantener |
| [Bucle autónomo acotado](bounded-autonomous-loop.es.md) | Seguridad de iterar sin supervisión | Fricción en cada turno |
| [Alertar en la ruta de fallback](alert-on-the-fallback-path.es.md) | Detectar degradación silenciosa | Más alertas que mantener honestas |
| [Una plataforma pequeña, muchos productos](shared-platform-blueprint.es.md) | Operabilidad de un portfolio; lecciones transferibles | Acoplamiento a una nube; superficie de fallo compartida |

# Validador · validar antes de construir

Una skill para revisar una tarea **antes** de pasársela a un agente de IA (o a una persona) para que la construya.

Un agente no pregunta: supone. Lo que la tarea no dice, lo inventa; lo que la tarea afirma mal, lo construye encima.
Corregir una tarea cuesta minutos; corregir lo que se construyó sobre ella cuesta la sesión entera y su revisión.

## Qué hace

Le das una tarea —un archivo, un issue o el texto— y la sesión:

1. **Comprueba contra el código real**, sin modificar nada, cada cosa que la tarea afirma: «esto no existe», «hay tres
   casos», «este servicio ya valida permisos». Lo que no cuadra lo corrige, con archivo y línea.
2. **Separa lo que pidió el cliente de lo que se dedujo.** Una deducción presentada como pedido es la forma más común de
   construir algo que nadie pidió.
3. **Resuelve las dudas técnicas** y las deja escritas con su porqué. **Las de negocio te las pregunta** en lenguaje
   llano: por qué hay que decidir, de dónde salió el requisito, las opciones con su costo, una recomendación y qué pasa
   si no se hace nada.
4. **Exige lo que un agente necesita para no adivinar:** qué no se toca, casos de prueba que fallen antes del cambio,
   criterios que no pasen solos y el ambiente donde se va a probar.
5. Termina con **«lista para construir»** o con la lista exacta de lo que falta y de quién depende.

Lo que **no** hace: escribir código. Quien valida no construye, y quien construye no valida su propio trabajo.

## Instalación

### Claude Code

```
/plugin marketplace add ing-valenzuela-galvan/validador
/plugin install validador@validador
```

Y en cualquier proyecto:

```
/validador:validar docs/tareas/T-014.md
/validador:validar 42          # un issue de GitHub
/validador:validar             # te pregunta qué validar
```

Sin instalar el plugin: copia `skills/validar/` a `~/.claude/skills/validar/` y se invoca como `/validar`.

### Otras herramientas (Cursor, Copilot, Codex, Gemini CLI…)

`skills/validar/SKILL.md` son instrucciones en texto plano. Agrégalo como regla o instrucciones del proyecto, o pégalo
al inicio de una conversación seguido de la tarea. Funciona mejor en una conversación aparte de la que va a construir.

## De dónde sale

Cada regla salió de algo que pasó en proyectos reales desarrollados con agentes de IA: tareas que daban por hecho cosas
que el código ya no hacía, requisitos que nadie pidió y pruebas en verde que no probaban nada.

## Licencia

MIT. Ver [LICENSE](LICENSE).

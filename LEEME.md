# Cómo publicar esta página — 10 minutos

Son dos archivos sueltos, sin dependencias ni compilación: HTML con los
estilos adentro. No cargan ninguna fuente, ningún script ni ninguna imagen de
afuera — lo cual, para una política de privacidad, no es un detalle menor:
nadie puede acusarte de rastrear a quien la lee.

```
index.html   la versión en inglés  ← la que Steam va a mirar
es.html      la versión en castellano
```

---

## Publicarla en GitHub Pages

1. Entrá a [github.com/new](https://github.com/new) y creá un repositorio
   **público** llamado `privacidad` (o `goblin-helper-privacy`, el nombre que
   quieras).

2. En la pantalla del repo vacío, hacé clic en **uploading an existing file**
   y arrastrá los dos `.html`. Escribí cualquier cosa como mensaje y dale a
   **Commit changes**.

3. Andá a **Settings → Pages** (menú de la izquierda).
   - En *Source*, elegí **Deploy from a branch**.
   - En *Branch*, elegí **main** y la carpeta **/ (root)**.
   - **Save**.

4. Esperá un par de minutos. GitHub te muestra arriba la dirección, con esta
   forma:

   ```
   https://TUUSUARIO.github.io/privacidad/
   ```

5. Abrila y comprobá que se ve bien. El castellano está en
   `.../privacidad/es.html`.

---

## Qué poner en Steam

En **Información básica → Enlaces externos → URL de política de privacidad**,
pegá la dirección en inglés:

```
https://TUUSUARIO.github.io/privacidad/
```

---

## Si después querés un dominio propio

Si algún día comprás `goblinhelper.com`, GitHub Pages acepta dominio propio
gratis desde esa misma pantalla de *Settings → Pages*, y la URL vieja sigue
redirigiendo. O sea que publicar ahora no te ata a nada.

---

## IMPORTANTE: esta página tiene que seguir siendo cierta

El texto no es genérico. Dice cosas concretas y comprobables sobre lo que la
app hace, sacadas del código:

- **los seis interruptores** salen de `goblin_sensores.FUENTES`, y que vengan
  apagados sale de `CONSENTIMIENTO_POR_DEFECTO`
- **que apagar borre lo recolectado** sale de `_olvidar_fuente` en
  `goblin_sensores.permitir`
- **la lista completa de hosts** sale de `goblin_security.ALLOWED_HOSTS`, que
  es la lista que la app aplica de verdad en cada salida a internet —de eso se
  ocupa `tests/test_egress.py`, con sus 50 comprobaciones
- **el séptimo interruptor**, el del contexto a la nube, sale de
  `ia_handler.puede_compartir_contexto`
- **dónde viven los datos** sale de `goblin_rutas.carpeta_datos`

Si mañana se agrega un proveedor de IA, una fuente de datos nueva o un host a
la lista, **esta página queda desactualizada y pasa a ser falsa**. Una política
de privacidad que no coincide con el programa es peor que no tener ninguna:
deja de ser una promesa y pasa a ser una declaración incorrecta.

La regla práctica: **si tocás `ALLOWED_HOSTS` o `FUENTES`, tocás esta página en
la misma tanda.**

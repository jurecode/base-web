# Base web

Base para cualquier dominio del hosting. Trae un panel de una sola caja: escribes
una palabra y el sitio sube o baja de GitHub, sin FTP y sin consola.

## Sitio nuevo

1. En GitHub, botón **Use this template** → un repositorio nuevo con el nombre del dominio.
2. Copia `config-ejemplo.php` como `config.php` y completa los cuatro datos
   (la dirección es la del repositorio nuevo, no la de esta plantilla).
3. Sube por FTP **sólo** `panel.php` y `config.php` a la raíz del dominio.
4. Entra a `eldominio.com/panel.php`, escribe la clave y luego `traer`:
   el resto del sitio baja solo.

De ahí en adelante, todo se hace con palabras desde el panel.

## Dominio que ya tiene sitio

Si la carpeta del dominio ya está funcionando, el paso 4 cambia: en vez de
`traer`, escribe **`instalar`**. Enlaza la carpeta con GitHub sin pisar nada
(sólo baja lo que falte), y después `subir` deja en GitHub el sitio tal como
está en el servidor.

## Palabras

| Palabra | Qué hace |
|---|---|
| `estado` | cómo está la carpeta y qué falta por subir |
| `subir` | guarda todo y lo manda a GitHub |
| `subir cambié el logo` | igual, pero deja escrito qué hiciste |
| `traer` | guarda lo tuyo y baja lo nuevo de GitHub |
| `traer github` | deja la carpeta igual que GitHub; lo de aquí queda guardado aparte |
| `instalar` | enlaza con GitHub un sitio que ya está en el servidor, sin pisar nada |
| `ayuda` | la lista de palabras |
| `salir` | cierra la sesión |

## Lo que el panel cuida solo

- El token nunca aparece en pantalla ni viaja a GitHub: vive únicamente en el
  `config.php` de cada servidor, y el panel se asegura de que quede ignorado.
- Si GitHub va más adelante, no deja subir encima: primero manda a `traer`.
- Si las dos partes cambiaron lo mismo, se detiene sin romper nada y ofrece
  `traer github`, que guarda lo del servidor en una rama `respaldo-fecha`.
- La primera vez, si un archivo del servidor fuera a ser pisado, git se detiene solo.

## Un repositorio por dominio

Cada sitio necesita el suyo: si dos dominios apuntaran al mismo, el `subir` de
uno pisaría el sitio del otro. Esta plantilla es sólo el punto de partida.

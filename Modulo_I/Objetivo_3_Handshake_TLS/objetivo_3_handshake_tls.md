# Objetivo 3: Handshake TLS

## ¿Qué es y cómo funciona el TLS Handshake?

Antes de que se envíe la primera petición HTTP, el navegador y el servidor tienen que ponerse de acuerdo en cómo cifrar la comunicación entre ambos. Ese proceso vendría a ser el **TLS Handshake**, o apretón de manos TLS.

Primero, el navegador le indica al servidor qué algoritmos de cifrado conoce y el servidor elige una opción compatible entre ambos. El servidor también manda su certificado digital, que contiene su clave pública.

El navegador corrobora que el certificado sea válido: que esté respaldado por una entidad certificadora de confianza, que no esté vencido y que corresponda al sitio al que se está conectando. Además, durante el handshake, el servidor demuestra que tiene la clave privada asociada al certificado. Así, el navegador verifica la identidad del servidor y se protege frente a un **man in the middle**, es decir, alguien que intenta hacerse pasar por el servidor en el medio de la comunicación.

Mediante un intercambio de claves basado en criptografía asimétrica, ambos acuerdan un secreto compartido del que derivan las claves de sesión. En TLS moderno, **no se envían directamente la clave de sesión**, sino que cada uno la calcula a partir del intercambio. La autenticación y el intercambio de claves forman parte del mismo handshake.

Luego de comprobar que el handshake se completó correctamente, comienzan a usar las claves de sesión con cifrado simétrico para operar con las requests y las respuestas HTTP.

## ¿Por qué se usan dos tipos de cifrado?

El cifrado simétrico y el asimétrico se diferencian por las claves que usan. El **simétrico usa una misma clave para cifrar y descifrar**. El **asimétrico usa un par de claves relacionadas: una pública y una privada**. Ese par también permite realizar firmas digitales y verificar la identidad del servidor.

Se usa el cifrado simétrico para las requests y las respuestas HTTP porque es más ligero computacionalmente y permite proteger muchos datos de forma eficiente. La criptografía asimétrica es más pesada, por eso se usa durante el handshake para autenticar al servidor y establecer las claves de forma segura, no para cifrar cada request HTTP.

De esta manera, se combinan los dos: la parte asimétrica permite establecer una comunicación segura y la simétrica permite mantenerla de forma rápida.

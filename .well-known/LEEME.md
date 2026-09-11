# Que hay aqui

Los dos ficheros que hacen que un enlace de `tamping.app` abra la app en vez
del navegador. Sin ellos, la configuracion de la app declara los enlaces y el
sistema los ignora: la confirmacion la tiene que dar el dominio.

## assetlinks.json — Android

Lleva la huella del certificado con el que se firma la app.

**Ojo cuando se publique en Google Play.** Play vuelve a firmar la app con una
clave suya, y a partir de ahi la huella que cuenta es la de Play, no esta. Hay
que anadirla a la lista -no sustituirla, porque las compilaciones internas
siguen usando la de arriba-. Se saca de:

    Play Console → tu app → Configuracion → Integridad de la aplicacion
    → Clave de firma de la aplicacion → SHA-256

## apple-app-site-association — iOS

Sin extension y sin comentarios: Apple lo lee tal cual.

Se sirve desde GitHub Pages, que no le pone `Content-Type: application/json`.
Apple lo acepta en la practica, pero si algun dia los enlaces dejan de abrir la
app en iOS, ese es el primer sitio donde mirar.

Para comprobarlo:

    curl -s https://tamping.app/.well-known/apple-app-site-association

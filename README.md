# Proyecto 2 - Ray tracing

Diorama de una pequena cabana hecho en Zig. Los rayos y los efectos se calculan en CPU; la API de Windows muestra los pixeles sin dependencias de terceros.

## Como correrlo

En Windows, con Zig 0.16.0:

```powershell
zig build run -Doptimize=ReleaseFast
```

`Esc` cierra la ventana.

## Avance

Dia 1: ventana con framebuffer de 320 x 240 pixeles, rayos en 3D, camara fija y una escena de prueba con bloques. Las caras tienen sombreado basico; las texturas y los efectos se agregaran en los siguientes avances.

Para comprobar los calculos:

```powershell
zig build test
```

## Video

Pendiente de grabar cuando esten terminados los materiales y efectos.

## Referencias del enunciado

- https://www.youtube.com/watch?v=91kxRGeg9wQ
- https://www.youtube.com/watch?v=WN98_qIKVds

# Comparación de conocimientos y aprendizajes
Antes de la práctica tenía conocimientos generales sobre contenedores, pero no comprendía bien la diferencia entre bind mounts, volúmenes nombrados y volúmenes anónimos.

Después de realizar la tarea entendí:
- Cómo montar carpetas locales en contenedores con bind mounts.
- Cómo crear volúmenes nombrados para mantener datos persistentes.
- Cómo funcionan los volúmenes anónimos y cuándo se eliminan.
- Cómo conectar contenedores en la misma red.
- Cómo revisar y limpiar volúmenes no utilizados.

# Problemas y soluciones
- Problema: El volumen no mostraba cambios al reiniciar el contenedor.
  Solución: Verifiqué la ruta correcta en -v y confirmé el montaje con "docker inspect".

- Problema: Error de conexión entre contenedores.
  Solución: Creé y usé una red personalizada con "docker network create" y usé el nombre del contenedor como host.

# Comandos adicionales usados
docker volume ls
docker inspect <contenedor>
docker network ls
docker logs <contenedor>

# Conclusión
La práctica fortaleció mi conocimiento en persistencia de datos en Docker, mejoró mi capacidad de resolver problemas prácticos y me acercó más a escenarios reales de despliegue de aplicaciones.


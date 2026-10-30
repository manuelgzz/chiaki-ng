# Android: controles táctiles y gamepad

Esta compilación conserva los cuatro parches de estabilidad y la configuración guardada de video/pacing.
Los cambios de controles se aplican después de esos parches mediante `android-controles-gamepad.patch`.
No ejecutar el paso antiguo que restaura StreamActivity desde 14955e5: cancelaba el colector de los botones visibles.

## Uso

1. Instalar el APK del workflow **Build Android Touch and Gamepad APK**.
2. En Ajustes → Gamepad, activar **Ocultar botones táctiles con gamepad** si se desea.
   Al desconectar el mando vuelven los controles que estaban habilitados. El modo solo touchpad sigue disponible.
3. En **Asignar botones del gamepad**, seleccionar el mando conectado y el botón de PS5 de destino.
4. Pulsar el botón físico. Para cruceta/gatillos analógicos, soltar y volver a pulsar.
   Las asignaciones se guardan por descriptor de mando y se aplican al iniciar la siguiente sesión.
5. **Quitar asignación** desactiva el destino. **Restaurar asignaciones predeterminadas** borra el perfil personalizado de ese mando.

Destinos: cruz, círculo, cuadrado, triángulo, cruceta, L1/R1/L2/R2/L3/R3, Options, Create/Share, PS y clic del touchpad.
Los sticks conservan su movimiento analógico. Los gatillos conservan su intensidad cuando se asignan a L2/R2.
Cada entrada física controla un destino; si se reasigna un botón ya usado, deja su acción anterior.
El clic del touchpad es asignable; los deslizamientos se hacen con el touchpad en pantalla.
El botón de silenciar micrófono no está expuesto por el protocolo de entrada Android de esta base.
Android puede interceptar PS/Home u otros botones del sistema antes de entregarlos a la app.

## Validación

El workflow ejecuta las pruebas JVM de asignación, visibilidad, persistencia y cancelación táctil,
las pruebas nativas de ciclo de vida/pacing, y genera un APK ARM64.
La interacción real multitáctil, conexión/desconexión Bluetooth/USB y la estabilidad en PS5
requieren validar el nuevo APK en la Y700.

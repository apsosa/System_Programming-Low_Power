### System Programming Low Power

Para este trabajo se utilizará como entorno de pruebas el programa
Bochs . El mismo permite simular
una computadora IBM-PC compatible desde el inicio, y realizar tareas de debugging. Todo el código
provisto para la realización del presente trabajo está ideado para correr en
Bochs
de forma sencilla.
Una computadora al iniciar comienza con la ejecución del POST y el BIOS, el cual se encarga
Floppy Disk como
boot-sector . El BIOS
se encarga de copiar a memoria 512 bytes del sector, a partir de la dirección 0x7C00 . Luego, se
comienza a ejecutar el código a partir esta dirección. El boot-sector debe encontrar en el floppy el
archivo KERNEL.BIN y copiarlo a memoria. Éste se copia a partir de la dirección 0x1200 , y luego se
de reconocer el primer dispositivo de booteo. En este caso dispondremos de un
dispositivo de booteo. En el primer sector de dicho
floppy ,
se almacena el
ejecuta a partir de esa misma dirección. En la figura 2 se presenta el mapa de organización de la
memoria utilizada por el
kernel .
Es importante tener en cuenta que el código del boot-sector se encarga exclusivamente de copiar
kernel y dar el control al mismo, es decir, no cambia el modo del procesador. El código del boot-
sector , como así todo el esquema de trabajo para armar el kernel y correr tareas, es provisto por la
el cátedra.
Los archivos a utilizar como punto de partida para este trabajo práctico son los siguientes:
− Makefile - encargado de compilar y generar el oppy disk.
- bochsrc y bochsdbg - configuración para inicializar Bochs.
- diskette.img - la imagen del flooppy que contiene el boot-sector preparado para cargar el kernel.
- kernel.asm - esquema básico del código para el kernel.
- defines.h y colors.h - constantes y definiciones.
- gdt.h y gdt.c - definición de la tabla de descriptores globales.
- tss.h y tss.c - definición de entradas de TSS.
- idt.h y idt.c - entradas para la IDT y funciones asociadas como idt_init para completar entradas en la IDT.
- isr.h y isr.asm - definiciones de las rutinas para atender interrupciones (Interrupt Service Routines).
- sched.h y sched.c - rutinas asociadas al scheduler.
- mmu.h y mmu.c - rutinas asociadas a la administración de memoria.
- screen.h y screen.c - rutinas para pintar la pantalla.
- a20.asm - rutinas para habilitar y deshabilitar A20.
- print.mac - macros útiles para imprimir por pantalla y transformar valores.
- idle.asm - código de la tarea Idle .
- game.h y game.c - implementación de los llamados al sistema y lógica del juego.
- syscalls.h - interfaz a utilizar desde las tareas para los llamados al sistema.
- kassert.h - rutinas para garantizar invariantes en el kernel.
- prng.c , prng.h y seed.c - generacion de numeros aleatorios.
- taskRick.c - código de las tareas del jugador Rick.
- taskMorty.c - código de las tareas del jugador Morty.
- i386.h - funciones auxiliares para utilizar assembly desde C.
- pic.c y pic.h - funciones pic_enable , pic_disable , pic_finish1 y pic_reset .

Aquí se realizo un circuito para encender un led utilizando el pic16f84a y el lenguaje ensamblador

LIST P=16F84A       ; Especificamos el modelo del PIC
    INCLUDE "P16F84A.INC" ; Archivo de inclusión con definiciones
    __CONFIG _CP_OFF & _WDT_OFF & _PWRTE_ON & _XT_OSC ; Configuración de bits
 
    ORG 0x00            ; Dirección de inicio del código
    GOTO START          ; Saltar a la etiqueta START
 
; CONFIGURACIÓN DE PUERTOS
START:
    BSF STATUS, RP0     ; Cambiar a banco 1 (acceso a configuración)
    CLRF TRISA          ; Configurar PORTA como salida
    BCF STATUS, RP0     ; Volver a banco 0 (modo operación)
 
    CLRF PORTA          ; Asegurar que PORTA inicie en 0
    BSF PORTA, 0        ; Encender LED en RA0 (mantenerlo encendido)
 
    END                 ; Fin del código

INICIO
    productos ← lista vacía

    ESCRIBIR "SISTEMA DE CONTROL DE ENVÍO DE ALIMENTOS"

    // 1. Cantidad de productos
    REPETIR
        LEER n
        SI n no es entero o n < 1 ENTONCES ESCRIBIR "Error"
    HASTA QUE n sea entero y n >= 1

    // 2. Registro de cada producto
    PARA i DESDE 1 HASTA n HACER
        REPETIR
            LEER nombre
            SI nombre está vacío ENTONCES ESCRIBIR "Error"
        HASTA QUE nombre no esté vacío

        REPETIR
            LEER dias
            SI dias no es entero o dias < 1 o dias > 365 ENTONCES
                ESCRIBIR "Error: debe estar entre 1 y 365"
        HASTA QUE dias sea entero y 1 <= dias <= 365

        AGREGAR (nombre, dias) A productos
    FIN PARA

    // 3. Ordenamiento de menor a mayor por días
    ordenados ← ORDENAR productos POR dias DE MENOR A MAYOR

    // 4. Salida
    ESCRIBIR "PLAN DE ENVÍO PRIORITARIO"
    posicion ← 1
    PARA CADA (nombre, dias) EN ordenados HACER
        ESCRIBIR posicion, ") ", nombre, " – ", dias, " días"
        posicion ← posicion + 1
    FIN PARA

    // 5. Verificación
    correcto ← VERDADERO
    PARA i DESDE 1 HASTA longitud(ordenados) - 1 HACER
        SI ordenados[i].dias > ordenados[i+1].dias ENTONCES
            correcto ← FALSO
    FIN PARA

    SI correcto ENTONCES ESCRIBIR "El orden es correcto"
    SINO ESCRIBIR "El orden es incorrecto"
FIN

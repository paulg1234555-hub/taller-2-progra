# taller-2-progra
#include <stdio.h>

int main() {
    float notas[5][3];
    float suma, prom, mayor, menor;
    int i, j, aprobados, reprobados;

    // Ingreso de notas con validación y mensaje de error
    for (i = 0; i < 5; i++) {
        printf("\nEstudiante %d:\n", i + 1);
        for (j = 0; j < 3; j++) {
            do {
                printf("  Nota de asignatura %d (0-10): ", j + 1);
                scanf("%f", &notas[i][j]);

                if (notas[i][j] < 0 || notas[i][j] > 10) {
                    printf("   Error: la nota debe estar entre 0 y 10.\n");
                }

            } while (notas[i][j] < 0 || notas[i][j] > 10);
        }
    }

    // Promedio, mayor y menor por estudiante
    printf("\n--- Promedio, mayor y menor por estudiante ---\n");
    for (i = 0; i < 5; i++) {
        suma = 0;
        mayor = menor = notas[i][0];
        for (j = 0; j < 3; j++) {
            suma += notas[i][j];
            if (notas[i][j] > mayor) mayor = notas[i][j];
            if (notas[i][j] < menor) menor = notas[i][j];
        }
        prom = suma / 3;
        printf("Estudiante %d -> Prom: %.2f | Mayor: %.2f | Menor: %.2f\n",
               i + 1, prom, mayor, menor);
    }

    // Promedio, mayor, menor y aprobados por asignatura
    printf("\n--- Promedio, mayor, menor y aprobados por asignatura ---\n");
    for (j = 0; j < 3; j++) {
        suma = 0;
        mayor = menor = notas[0][j];
        aprobados = reprobados = 0;
        for (i = 0; i < 5; i++) {
            float n = notas[i][j];
            suma += n;
            if (n > mayor) mayor = n;
            if (n < menor) menor = n;
            if (n >= 6)
                aprobados++;
            else
                reprobados++;
        }
        prom = suma / 5;
        printf("Asignatura %d -> Prom: %.2f | Mayor: %.2f | Menor: %.2f | Aprob: %d | Reprob: %d\n",
               j + 1, prom, mayor, menor, aprobados, reprobados);
    }

    return 0;
}

#include <stdio.h>

#define SIZE 9


int verificar_linha(int matriz[SIZE][SIZE], int linha) {
    int numeros[SIZE + 1] = {0};
    for (int i = 0; i < SIZE; i++) {
        int num = matriz[linha][i];
        if (num < 1 || num > 9 || numeros[num]) return 0; 
    }
    return 1;  
}


int verificar_coluna(int matriz[SIZE][SIZE], int coluna) {
    int numeros[SIZE + 1] = {0};
    for (int i = 0; i < SIZE; i++) {
        int num = matriz[i][coluna];
        if (num < 1 || num > 9 || numeros[num]) return 0;  
        numeros[num] = 1;
    }
    return 1; 
}


int verificar_subgrade(int matriz[SIZE][SIZE], int inicio_linha, int inicio_coluna) {
    int numeros[SIZE + 1] = {0};
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            int num = matriz[inicio_linha + i][inicio_coluna + j];
            if (num < 1 || num > 9 || numeros[num]) return 0;  
            numeros[num] = 1;
        }
    }
    return 1;  
}


int verificar_sudoku(int matriz[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        if (!verificar_linha(matriz, i) || !verificar_coluna(matriz, i)) {
            return 0;  
        }
    }
    
    for (int i = 0; i < SIZE; i += 3) {
        for (int j = 0; j < SIZE; j += 3) {
            if (!verificar_subgrade(matriz, i, j)) {
                return 0;  
            }
        }
    }
    return 1;  
}

int main() {
    int n;
    scanf("%d", &n);
    
    for (int k = 1; k <= n; k++) {
        int matriz[SIZE][SIZE];
        
        
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                scanf("%d", &matriz[i][j]);
            }
        }
        
       
        printf("Instancia %d\n", k);
        
        
        if (verificar_sudoku(matriz)) {
            printf("SIM\n");
        } else {
            printf("NAO\n");
        }
        
        
        printf("\n");
    }
    
    
}

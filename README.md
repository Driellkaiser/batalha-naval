# batalha-naval
Posicionando Navios no Tabuleiro
```
#include <stdio.h>

#define TAMANHO_TABULEIRO 10
#define TAMANHO_NAVIO 3

int main() {
    // ---------- Inicializar o tabuleiro ----------
    int tabuleiro[TAMANHO_TABULEIRO][TAMANHO_TABULEIRO];
    for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
        for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
            tabuleiro[i][j] = 0; // 0 representa água
        }
    }

    // ---------- Definir os navios ----------
    int navio1[TAMANHO_NAVIO] = {3, 3, 3}; // Horizontal
    int navio2[TAMANHO_NAVIO] = {3, 3, 3}; // Vertical

    // ---------- Coordenadas iniciais ----------
    int linhaNavio1 = 2;
    int colunaNavio1 = 1;

    int linhaNavio2 = 5;
    int colunaNavio2 = 7;

    // ---------- Validar se o posicionamento é possível ----------
    // Navio horizontal: verifica se cabe na linha e não ultrapassa
    if (colunaNavio1 + TAMANHO_NAVIO <= TAMANHO_TABULEIRO) {
        // Verifica se as posições estão livres (sem sobreposição)
        int sobreposicao = 0;
        for (int i = 0; i < TAMANHO_NAVIO; i++) {
            if (tabuleiro[linhaNavio1][colunaNavio1 + i] != 0) {
                sobreposicao = 1;
                break;
            }
        }

        if (!sobreposicao) {
            for (int i = 0; i < TAMANHO_NAVIO; i++) {
                tabuleiro[linhaNavio1][colunaNavio1 + i] = navio1[i];
            }
        }
    }

    // Navio vertical: verifica se cabe na coluna e não ultrapassa
    if (linhaNavio2 + TAMANHO_NAVIO <= TAMANHO_TABULEIRO) {
        // Verifica se as posições estão livres (sem sobreposição)
        int sobreposicao = 0;
        for (int i = 0; i < TAMANHO_NAVIO; i++) {
            if (tabuleiro[linhaNavio2 + i][colunaNavio2] != 0) {
                sobreposicao = 1;
                break;
            }
        }

        if (!sobreposicao) {
            for (int i = 0; i < TAMANHO_NAVIO; i++) {
                tabuleiro[linhaNavio2 + i][colunaNavio2] = navio2[i];
            }
        }
    }

    // ---------- Exibir o tabuleiro ----------
    printf("Tabuleiro Batalha Naval:\n\n");
    for (int i = 0; i < TAMANHO_TABULEIRO; i++) {
        for (int j = 0; j < TAMANHO_TABULEIRO; j++) {
            printf("%d ", tabuleiro[i][j]);
        }
        printf("\n");
    }

    return 0;
}

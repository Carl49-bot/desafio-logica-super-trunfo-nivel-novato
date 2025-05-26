# DESAFIO LÓGICA SUPER TRUNFO NIVEL NOVATO

#include <stdio.h>
#include <string.h>


# Definição da estrutura da carta:

struct Carta {
    char estado[30];
    char codigo[10];
    char cidade[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadePopulacional;
    float pibPerCapita;
};

# Função para cadastrar os dados da carta:

void cadastrarCarta(struct Carta *carta, int numero) {
    printf("\n--- Cadastro da Carta %d ---\n", numero);

    printf("Informe o Estado: ");
    scanf(" %[^\n]", carta->estado);

    printf("Informe o Código da carta: ");
    scanf(" %[^\n]", carta->codigo);

    printf("Informe o Nome da cidade: ");
    scanf(" %[^\n]", carta->cidade);

    printf("Informe a População: ");
    scanf("%d", &carta->populacao);

    printf("Informe a Área (em km²): ");
    scanf("%f", &carta->area);

    printf("Informe o PIB (em milhões): ");
    scanf("%f", &carta->pib);

    printf("Informe o Número de pontos turísticos: ");
    scanf("%d", &carta->pontosTuristicos);

    // Calculando os valores derivados
    carta->densidadePopulacional = carta->populacao / carta->area;
    carta->pibPerCapita = carta->pib / carta->populacao;
}

# Função para comparar duas cartas com base em um único atributo:

void compararCartas(struct Carta c1, struct Carta c2) {

    // Aqui você escolhe o atributo fixo para comparação:
    const char atributo[] = "populacao"; // Troque para: "area", "pib", "densidade", "pibPerCapita"

    printf("\n🔍 Comparação de Cartas (Atributo: %s)\n", atributo);

    float valor1, valor2;
    int vencedor = -1;

    // Comparação com base no atributo escolhido
    if (strcmp(atributo, "populacao") == 0) {
        valor1 = c1.populacao;
        valor2 = c2.populacao;
        vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;

    } else if (strcmp(atributo, "area") == 0) {
        valor1 = c1.area;
        valor2 = c2.area;
        vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;

    } else if (strcmp(atributo, "pib") == 0) {
        valor1 = c1.pib;
        valor2 = c2.pib;
        vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;

    } else if (strcmp(atributo, "densidade") == 0) {
        valor1 = c1.densidadePopulacional;
        valor2 = c2.densidadePopulacional;
        vencedor = (valor1 < valor2) ? 1 : (valor1 > valor2) ? 2 : 0; // Menor vence!

    } else if (strcmp(atributo, "pibPerCapita") == 0) {
        valor1 = c1.pibPerCapita;
        valor2 = c2.pibPerCapita;
        vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;
    }

    printf("\n📊 Carta 1 - %s (%s): %.2f\n", c1.cidade, c1.estado, valor1);
    printf("📊 Carta 2 - %s (%s): %.2f\n", c2.cidade, c2.estado, valor2);

    if (vencedor == 1)
        printf("\n🏆 Resultado: Carta 1 (%s) venceu!\n", c1.cidade);
    else if (vencedor == 2)
        printf("\n🏆 Resultado: Carta 2 (%s) venceu!\n", c2.cidade);
    else
        printf("\n🤝 Resultado: Empate!\n");
}

int main() {
    struct Carta carta1, carta2;

    printf("=======================================\n");
    printf("     Bem-vindo ao Super Trunfo Cidades \n");
    printf("           Nível: Novato 🎯\n");
    printf("=======================================\n");

    cadastrarCarta(&carta1, 1);
    cadastrarCarta(&carta2, 2);

    compararCartas(carta1, carta2);

    printf("\nObrigado por jogar! 🌍\n");

    return 0;
}

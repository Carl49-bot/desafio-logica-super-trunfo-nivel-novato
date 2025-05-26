# DESAFIO LÓGICA SUPER TRUNFO 
# 1 - Nivel Novato

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


# 2 - Nivel Aventureiro

#include <stdio.h>
#include <string.h>

struct Carta {
    char pais[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadeDemografica;
};

# Função para cadastrar os dados da carta:
void cadastrarCarta(struct Carta *carta, int numero) {
    printf("\n--- Cadastro da Carta %d ---\n", numero);

    printf("Nome do país: ");
    scanf(" %[^\n]", carta->pais);

    printf("População: ");
    scanf("%d", &carta->populacao);

    printf("Área (em km²): ");
    scanf("%f", &carta->area);

    printf("PIB (em bilhões): ");
    scanf("%f", &carta->pib);

    printf("Número de pontos turísticos: ");
    scanf("%d", &carta->pontosTuristicos);

    // Cálculo da densidade
    carta->densidadeDemografica = carta->populacao / carta->area;
}

void compararAtributo(struct Carta c1, struct Carta c2, int escolha) {
    float valor1, valor2;
    int vencedor = -1;
    char atributo[30];

    switch (escolha) {
        case 1:
            valor1 = c1.populacao;
            valor2 = c2.populacao;
            strcpy(atributo, "População");
            vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;
            break;
        case 2:
            valor1 = c1.area;
            valor2 = c2.area;
            strcpy(atributo, "Área");
            vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;
            break;
        case 3:
            valor1 = c1.pib;
            valor2 = c2.pib;
            strcpy(atributo, "PIB");
            vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;
            break;
        case 4:
            valor1 = c1.pontosTuristicos;
            valor2 = c2.pontosTuristicos;
            strcpy(atributo, "Pontos Turísticos");
            vencedor = (valor1 > valor2) ? 1 : (valor1 < valor2) ? 2 : 0;
            break;
        case 5:
            valor1 = c1.densidadeDemografica;
            valor2 = c2.densidadeDemografica;
            strcpy(atributo, "Densidade Demográfica");
            vencedor = (valor1 < valor2) ? 1 : (valor1 > valor2) ? 2 : 0; // menor vence
            break;
        default:
            printf("Opção inválida!\n");
            return;
    }

    printf("\n🔍 Comparação de Cartas (Atributo: %s)\n", atributo);
    printf("Carta 1 - %s: %.2f\n", c1.pais, valor1);
    printf("Carta 2 - %s: %.2f\n", c2.pais, valor2);

    if (vencedor == 1)
        printf("\n🏆 Resultado: Carta 1 (%s) venceu!\n", c1.pais);
    else if (vencedor == 2)
        printf("\n🏆 Resultado: Carta 2 (%s) venceu!\n", c2.pais);
    else
        printf("\n🤝 Resultado: Empate!\n");
}

int main() {
    struct Carta carta1, carta2;
    int escolha;

    printf("=======================================\n");
    printf("     Super Trunfo Países 🌎 - Nível Aventureiro\n");
    printf("=======================================\n");

    cadastrarCarta(&carta1, 1);
    cadastrarCarta(&carta2, 2);

    printf("\nEscolha o atributo para comparar:\n");
    printf("1 - População\n");
    printf("2 - Área\n");
    printf("3 - PIB\n");
    printf("4 - Pontos Turísticos\n");
    printf("5 - Densidade Demográfica\n");
    printf("Digite sua opção: ");
    scanf("%d", &escolha);

    compararAtributo(carta1, carta2, escolha);

    return 0;
}

# 3 - Nivel Mestre

#include <stdio.h>
#include <string.h>

struct Carta {
    char pais[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadeDemografica;
};

# Cálculo da densidade
void cadastrarCarta(struct Carta *carta, int numero) {
    printf("\n--- Cadastro da Carta %d ---\n", numero);

    printf("Nome do país: ");
    scanf(" %[^\n]", carta->pais);

    printf("População: ");
    scanf("%d", &carta->populacao);

    printf("Área (em km²): ");
    scanf("%f", &carta->area);

    printf("PIB (em bilhões): ");
    scanf("%f", &carta->pib);

    printf("Número de pontos turísticos: ");
    scanf("%d", &carta->pontosTuristicos);

    carta->densidadeDemografica = carta->populacao / carta->area;
}

float obterValor(struct Carta carta, int atributo) {
    switch (atributo) {
        case 1: return carta.populacao;
        case 2: return carta.area;
        case 3: return carta.pib;
        case 4: return carta.pontosTuristicos;
        case 5: return carta.densidadeDemografica;
        default: return 0;
    }
}

int compararValores(float v1, float v2, int atributo) {
    if (atributo == 5) // Densidade: menor vence
        return (v1 < v2) ? 1 : (v1 > v2) ? 2 : 0;
    else
        return (v1 > v2) ? 1 : (v1 < v2) ? 2 : 0;
}

const char* nomeAtributo(int atributo) {
    switch (atributo) {
        case 1: return "População";
        case 2: return "Área";
        case 3: return "PIB";
        case 4: return "Pontos Turísticos";
        case 5: return "Densidade Demográfica";
        default: return "Desconhecido";
    }
}

int main() {
    struct Carta c1, c2;
    int a1, a2;

    printf("=============================================\n");
    printf("     Super Trunfo Mestre 🔥 - Comparação Avançada\n");
    printf("=============================================\n");

    cadastrarCarta(&c1, 1);
    cadastrarCarta(&c2, 2);

    printf("\nEscolha dois atributos diferentes para comparar:\n");
    printf("1 - População\n");
    printf("2 - Área\n");
    printf("3 - PIB\n");
    printf("4 - Pontos Turísticos\n");
    printf("5 - Densidade Demográfica\n");

    do {
        printf("Primeiro atributo: ");
        scanf("%d", &a1);
        printf("Segundo atributo: ");
        scanf("%d", &a2);
        if (a1 == a2) printf("⚠️ Atributos devem ser diferentes!\n");
    } while (a1 == a2);

    float v1a1 = obterValor(c1, a1);
    float v2a1 = obterValor(c2, a1);

    float v1a2 = obterValor(c1, a2);
    float v2a2 = obterValor(c2, a2);

    float soma1 = v1a1 + v1a2;
    float soma2 = v2a1 + v2a2;

    printf("\n🔍 Comparação usando dois atributos:\n");
    printf("%s:\n", nomeAtributo(a1));
    printf(" - %s: %.2f\n", c1.pais, v1a1);
    printf(" - %s: %.2f\n", c2.pais, v2a1);

    printf("%s:\n", nomeAtributo(a2));
    printf(" - %s: %.2f\n", c1.pais, v1a2);
    printf(" - %s: %.2f\n", c2.pais, v2a2);

    printf("\nSoma dos atributos:\n");
    printf(" - %s: %.2f\n", c1.pais, soma1);
    printf(" - %s: %.2f\n", c2.pais, soma2);

    if (soma1 > soma2)
        printf("\n🏆 Resultado: Carta 1 (%s) venceu!\n", c1.pais);
    else if (soma2 > soma1)
        printf("\n🏆 Resultado: Carta 2 (%s) venceu!\n", c2.pais);
    else
        printf("\n🤝 Resultado: Empate!\n");

    return 0;
}



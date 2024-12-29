#include <cs50.h>
#include <stdio.h>
#include <math.h>

int main(void)
{
    float reais;
    // Solicita ao usuário a entrada do valor devido até que seja válida (não negativa)
    do
    {
        reais = get_float("Troca devida: ");
    } while (reais < 0);

    // Converte reais para centavos e arredonda corretamente
    int centavos = round(reais * 100);

    // Inicializa o número de moedas como 0
    int moedas = 0;

    // Define os valores das moedas disponíveis (em centavos)
    int valores[] = {25, 10, 5, 1};

    // Calcula o número mínimo de moedas necessário
    for (int i = 0; i < 4; i++)
    {
        moedas += centavos / valores[i];
        centavos %= valores[i];
    }

    // Imprime o número mínimo de moedas
    printf("%d\n", moedas);

    return 0;
}

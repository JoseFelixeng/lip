### Aula 8 e 9

O setfill serve para escolher o caractere e o setw fixa N caracteres na saída Daí, no caso que te mandei, ele mantêm 8, dos 10 'x' que ele fixa e os outros 2, são substituídos pela saída 77 essa vai ser a ideia para o relógio da sua questão.





### Exemplo:

```C++
/******************************************************************************************************
Horas do diaFaça uma função que recebe como entrada uma quantidade de tempo em segundos transcorrida ao
longo de um dia e a imprime no formato HH:MM:SS. Por exemplo, se o tempo de 78210 segundos foram
transcorridos ao longo do dia, então a hora atual é 21:43:30.Dica:Utilize a biblioteca "iomanip" e as
funções setfill(), setw(). Exemplo:cout<
***********************************************/

#include <iostream>
#include <iomanip>

using namespace std;

void conversor(int s)
{
    int hora, minuto, segundo;

    hora = s / 3600;
    minuto = (s % 3600) / 60;
    segundo = ((s % 3600) % 60);

    cout << "A hora é ==> ";
    cout << setfill('0') << setw(2) << hora << ":";

    cout << setfill('0') << setw(2) << minuto << ":";

    cout << setfill('0') << setw(2) << segundo << endl;
}
int main()
{
    int n;

    cout << "Digite um valor em segundos: ";

    cin >> n;

    conversor(n);
    return 0;
}

```
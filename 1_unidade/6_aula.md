### Modularização com arquivos .h

```C++

#ifndef MMCMDC_H

#define MMCMDC_H

void computa_mdc_mmc ( int x , int y , int & mdc , int & mmc ) ;
int computa_mdc ( int x , int y ) ;
int computa_mmc ( int x , int y ) ;

endif // MMC - MDC_H_INCLUDED

Esse é um exemplo de encapsulamento externo para o uso de um arquivo separado apenas com as funções de um dado programa dessa forma no arquivo .h ficam as funções em quanto no arquivo .cpp os mesmo estarão disponibilizados como um programa.

#include " MMCMDC . h "

void computa_mdc_mmc ( int x , int y , int & mdc , int & mmc ) {
mdc = computa_mdc (x , y ) ;
mmc = computa_mmc (x , y ) ;
}

int computa_mdc ( int x , int y ) {
int mdc ;
if ( x < y ) {
mdc = x ;
}
else {
mdc = y ;
}
while ( x % mdc != 0 || y % mdc != 0) {
mdc - -;
}
return mdc ;
}

int computa_mmc ( int x , int y ) {
int mmc ;
if ( x < y ) {
mmc = y ;
}
else {
mmc = x ;
}
while ( mmc % x != 0 || mmc % y != 0) {
mmc ++;
}
return mmc ;

```





### O arquivo main




```C++
#include < iostream >

#include " MMCMDC . h "

using namespace std ;

int main ()
{
int x , y , mdc , mmc ;
cout << " Insira dois numeros :\\ n " ;
cin >> x >> y ;
computa_mdc_mmc (x , y , mdc , mmc ) ;
cout << " MDC : " << mdc << endl ;
cout << " MMC : " << mmc << endl ;
return 0;

```




No arquivo MMCMDC.h se encontram as assinaturas das funções que serão implementadas em umcarquivo .cpp separado. A primeira parte do código que chama a atenção são as diretivas `#ifndef` e `#endif` . Elas devem ser usadas em conjunto, e devem envolver toda a declaração das assinaturas no arquivo .h . Essas diretivas são utilizadas para verificar se já existe uma definição anterior das funções declaradas no arquivo .h . Caso não exista, a diretiva `#define` é executada, inserindo o arquivo MMCMDC.h . Caso já exista, a diretiva não é executada, e a declaração anterior prevalece. Isto evita erros de compilação por múltiplas definições do mesmo arquivo.

No arquivo MMCMDC.cpp se encontram as implementações das funções declaradas no arquivo MMCMDC.h.O arquivo.cpp deve ter o mesmo nome do arquivo .h associado. No início de MMCMDC.cpp usamos a diretiva `#include` para inserir o arquivo MMCMDC.h , entre aspas duplas: isto é necessário para permitir a integração da implementação com o as assinaturas no arquivo com a função principal.




### Exemplos:

```C++
O arquivo main

/******************************************************************************
Inverte X: Escreva uma função que recebe como parâmetro um número inteiro x.
A função deve utilizar um parâmetro por referência para informar o valor de x
invertido (por exemplo, 123 -> 321). A função também deve retornar: * -1 se o número
x é menor que o número x invertido ; * 0 se x e o número invertido são iguais;
* 1 caso contrario. Seu programa deve imprimir o valor de x, x invertido e uma
* frase informando se x é maior, menor ou igual ao seu valor invertido.
X = 4001
X invertido = 1004
X é maior que X invertido
*******************************************************************************/

#include <iostream>

using namespace std;

void inverte(int &x) {
    int n = x;
    int inv = 0;
    int cont = 0;
    while (n > 0) {
        inv = 10 * inv + n % 10;
        n /= 10;
    }

    cout << "X: " << x << endl;
    cout << "invertido: " << inv << endl;
    cout << endl;

    if(inv == x){
        cont = 0;
    }else if(inv < x){
        cont = -1;
    }else{
        cont = 1;
    }
    cout << "Valor: " << cont << endl;
    cout << endl;

    if(cont == -1){
        cout << "X = " << x << endl;
        cout << "X invertido = " << inv << endl;
        cout << "X é maior que X invertido" << endl;
    }else if(cont == 1){
        cout << "X = " << x << endl;
        cout << "X invertido = " << inv << endl;
        cout <<"X é menor que X invertido" << endl;

    }else if(cont == 0){
        cout << "X = " << x << endl;
        cout << "X invertido = " << inv << endl;
        cout << "X é igual que X invertido" << endl;
    }
}

int main()
{
    int n;

    cout << "Insira um numero: ";
    cin >> n;

    inverte(n);

    return 0;
}

```

```C++
/*
Horas do diaFaça uma função que recebe como entrada uma quantidade de tempo em segundos transcorrida ao longo de um dia e,
utilizando parâmetros por referência, retorne o número de horas, minutos e segundos que representa esse número. Por exemplo,
se o tempo de 78210 segundos foram transcorridos ao longo do dia, então a hora atual é 21:43:30.Utilizando essa função,
implemente outra função que recebe como entrada uma quantidade de tempo em segundos transcorrida ao longo de um dia e
imprime na tela o período do dia correspondente: - Madrugada (00:00 às 05:59)- Manhã: (6:00 às 11:59)- Tarde (12:00 às 17:59)-
Noite (18:00 às 23:59)
*/

#include <iostream>

using namespace std;

void periodo(int t);

int main(){

    int t;

    cin >> t;

    periodo(t);

}

void periodo(int t)
{
    if(t >= 0 && t <= 21540)
        cout << "Madrugada";

    else if(t >= 21600 && t <= 43140)
        cout << "Manhã";

    else if (t >= 43200 && t <= 64740)
        cout << "Tarde";

    else if(t >= 64800)
        cout << "Noite";
}

```







### Aula de Exercícios

```C++
## Codigo da aula

/******************************************************************************
Implemente uma função que recebe os coeficientes a, b e c de uma equação de segundo grau e retorne:
===>Quantas raízes reais esta equação possui;
===>Retorne o valor de suas raízes  reais, caso existam;

#Valores para teste:
=> a =   1
=> b =  -1
=> c = -12

#Resultado experado:
=>x1 =  4
=>x2 = -3
******************************************************************************/

#include <iostream>
#include <cmath>

using namespace std;

int resolverEquacao(float a, float b, float c, float &x1, float &x2);

int main()
{
float a, b, c , raiz1 , raiz2;

int qtd;

cout << "Informe os coeficientes a, b, c: ";

cin >> a >> b >> c;

qtd = resolverEquacao(a, b, c, raiz1, raiz2);

if(qtd == 0){
    cout << "Sem raizes Reais. " << endl;
}else if (qtd == 1){
    cout << "Uma raiz: " << raiz1 << endl;
}else {
    cout << "Duas raizes: " << raiz1 << " & " << raiz2 << endl;
}

return 0;

}

int resolverEquacao(float a, float b, float c, float &x1, float &x2){

float delta = b*b - 4*a*c;

if(delta < 0){
        return 0;
}else if (delta == 0){
    x1 = x2 = -b/(2*a);

    return 1;
}else {
    x1 = (-b + sqrt(delta))/(2*a);

    x2 = (-b - sqrt(delta))/(2*a);

    return 2;
}
}

```
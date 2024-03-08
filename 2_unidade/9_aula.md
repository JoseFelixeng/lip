# Unidade 2

### Aula 10 - Vetores

Vetores(Arrays)

- Conjunto de variáveies de mesmo tipo, agrupadas sob o mesmo identificador;
- Elementos acessados por índice;
- Ordem Linear;

Declaração:

``` int c[12]; float f[500]; ``` 

A capacidade do array deve sempre ser um valor constante(inteiro). Inicialização de um array: 

1. Declara array n com 10 elementos // Inteiros e os inicializa com 0 int n[10] = {0};

2. Declara array b com capacidade de 10 elementos //e os inicializa com o valor informado int b[10] = {10,20,30,40,50,60,70,80,90,100};

3. Declara o array z com a capacidade igual //ao número de elementos usados na inicialização float z [ ] = {3.0,1.2,3.98};

### Exemplos:



 # Problema 1 #
 **Armazenar as notas den alunos. Para as notas armazenadas, calcular a média e informar quantos  alunos têm nota acima da média.**



```C++

#include <iostream>
#define MAX 100

using namespace std;

int main()
{
    float notas[MAX], soma = 0, media;
    int n, cont = 0;

    cout << "Informe a quantidade de notas: ";

    cin >> n;

    cout << "Informe " << n << " notas: " << endl;

    //for usado para receber as notas;
    for (int i = 0; i < n; i++)
    {
        cin >> notas[i];
    }

    cout << "Notas informadas: " << endl;

    //for usado para mostrar  as notas recebidas anteriomente.
    for (int i = 0; i < n; i++)
    {
        cout << notas[i] << " ";
    }
    //for usado para calcular as notas a cada indice

    for (int i = 0; i < n; i++)
    {
        soma = soma + notas[i];
    }
    media = soma / n;

    cout << "Media = " << media << endl;

    // for usado para encontrar os valores acima da média

    for (int i = 0; i < n; i++)
    {
        if (notas[i] > media)
        {
            cont++;
        }
    }

    cout << "Acima da media: " << cont << endl;

    return 0;
}

```




# Problema 2 #

**Dados dois vetores u e v seu produto escalar:**

    u*v é dado por u*v = Somatorio{(i=1,n)ui*vi} = u1*v1 + u2v2 + u3v3 ... + un + vn;

**Crie um programa para calcular o produto escalar de dois vetores informados pelo usuário.**




```C++


#include <iostream>
#define MAX 100

using namespace std;

int main()
{
    int u[MAX], v[MAX], escalar = 0;
    int n;

    cout << "Informe a quantidade de componentes dos vetores: ";

    cin >> n;

    cout << "Informe os valores de u: ";

    // for usado para receber todos os valores de u;
    for (int i = 0; i < n; i++)
    {
        cin >> u[i];
    }
    cout << "Informe os valores de v: ";
    // for usado para receber todos os valores de v;
    for (int i = 0; i < n; i++)
    {
        cin >> v[i];
    }

    // for usado para pecorrer todos os valores de u e v dentro dos vetores;

    for (int i = 0; i < n; i++)
    {
        escalar += u[i] * v[i];
    }

    cout << "Escalar: " << escalar << endl;
    return 0;
}

```




# Problema 3 #

**Dado um vetor com 5 elementos, gere um segundo vetor, correspondente à inversão da ordem de seus elementos. Mostre o resultado na tela.**


```C++


#include <iostream>

using namespace std;

int main()
{
    int a[5] = {1, 2, 3, 4, 5};
    int b[5];

    //for usado para percorrer ambos os vetores tanto a quanto b;

    for (int i = 0, j = 4; i < 5; i++, j--)
    {
        b[j] = a[i];
    }

    cout << "Inversão de a: ";

    //for usado para mostrar o resultado na tela percorrendo o indic b

    for (int i = 0; i < 5; i++)
    {
        cout << b[i] << " ";
    }
    return 0;
}

```



# Problema 4 #

**Solicite ao usuário um vetor de inteiros com n elementos e imprima na tela seus valores excluindo-se duplicatas.**


```C++


#include <iostream>
#define MAX 100
using namespace std;

int main(){
    int v[MAX], n;

    cout << "Informe o valor de n: ";

    cin >> n;

    cout << "Informe os valores do vetor: ";

    //for usado para gerar todos os indices do vetor correspondentes as entradas.

    for(int i = 0;i < n;i++){
        cin >> v[i];
    }

    //algoritmo usado para verificar se um numero foi repetido ou não;
    //for usado para percorrer o vetor do indice 0 até n-1 em busca de um numero que foi repetido a esquerda , para que esse numero não seja impresso;
// a variavel bool vai ser usada como para parametro para saber se no indice indicado o numero atual já foi impresso;
bool flag;
for(int i = 0;i < n;i++){
    flag = false;

 //for usado para fazer uma busca no vetor em busca de numeros repetidos;
    for(int j = 0 ;j < i ;j++){
    //if usado para encontrar uma duplicata do valor
        if(v[i]==v[j]){
            flag = true;
            break;
     }
    }
    //if usado para dizer que foi encontrado uma duplicata
    if(flag == false){
        cout << "Numeros não repetidos: " << v[i] << endl;
    }
}

    return 0;
}

```


# Problema #
**Ordem-inversa Leia n (n <= 30) números e imprima-os na ordem inversa.**



```C++


#include <iostream>
#define MAX 30

using namespace std;

int main()
{
    int a[MAX];
    int b[MAX];
    int c;
//a variavel c determina a quantidade de entradas do programa
    cin >> c;

// for usado para inserir valores no vetor A
    for(int i=0;i < c;i++){
        cin >> a[i];
    }
// for usado para incrementar o vetorB na ordem inversa ao vetorA
    for (int i = 0, j = c-1; i < c; i++, j--)
    {
        b[j] = a[i];
    }

//for usado para imprimir os valores do vetorB para cada entrada;
    for (int i = 0; i < c; i++)
    {
        cout << b[i] << endl;
    }
    return 0;
}

```



# Problema 6 #

**Elemento repetido  Leia uma sequência de n (n <= 20) números e informe se existe algum elemento repetido na sequência.**



```C++




#include <iostream>
#define MAX 20

using namespace std;

int main()
{
    int vetor[MAX], n, menor, m;
    bool achou;

    cout << "Digite numero de repetição: ";
    cin >> n;

    cout << "Digite os valores: ";
    for(int i = 0;i < n;i++){
        cin >> vetor[i];
    }
    menor = 0;

    for(int i = 0;i < n;i++){
        if(vetor[i] == menor){
            achou = true;
            m = menor;
        }
       menor = vetor[i];
    }
    if(achou){
        cout << "Existem elementos repetidos" << endl;
    }else{
        cout << "Não repetiu:" << menor << endl;
    }
    return 0;
}

```
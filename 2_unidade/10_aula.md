# Aula 10 

Nessa aula foi feito e debatido varios exemplos em C++.



# Exemplo 1

**O setor de vendas de uma loja precisa saber quantas vendas ocorreram com um determinado valor. Para isto,
inicialmente escreva um programa que deve ler o número de vendas (n <= 10) e sua respectiva lista de valores
inteiros associados, armazenando-os em um vetor. Em seguida, deve ser possível consultar quantas vendas ocorreram
com um determinado valor passado na entrada do programa. Veja o exemplo a seguir:**

```
Entrada: 

10
1
2
9
4
5
9
7
8
9
10
9
```




```C++


#include <iostream>
#define MAX 10
using namespace std;

int main()
{
    int vetorVendas[MAX];
    int nv, valor, cont = 0;
    bool achei = false;

    cout << "Quantas Vendas: ";
    cin >> nv;

    for(int i = 0;i < nv ;i++){
        cin >> vetorVendas[i];
    }

    for(int i = 0;i < nv;i++){
        cout << vetorVendas[i]<< " ";
    }

    cout << "Valor Buscado: ";
    cin >> valor;
    for (int i = 0; i < nv; i++)
    {
        if (vetorVendas[i] == valor)
        {
            cont++;
            achei = true;
        }
    }
    if(achei == true){
        cout << "Houve venda " << cont << endl;
    }else if(achei == false){
        cout << "Nao houve vendas com o valor " << valor << endl;
    }

    return 0;
}

```

# Exemplo 2
 

**Você deve escrever um programa que lê os elementos de um vetor e um número inteiro X e
imprime uma mensagem indicando se há dois elementos no vetor cuja soma é igual a X. Abaixo
temos um exemplo de entrada e saída, onde o primeiro valor inteiro representa 2 <= N <= 20
indica o número de elementos do vetor. Em seguida, temos os N elementos do vetor, e finalmente
o valor de X.**


```
Exemplo 1:
Entrada:
				{N.de elementos}  [valor da localização]            {A ser comparado}
				{4}                 [1 5 6 12]                             {6}
				{10}                [50 40 10 2 30 1 5 2 5 3]              {4}
				{4}                 [1 5 6 12]                             {12}
				{4}                 [1 5 6 12]                             {17}

```

```C++

#include <iostream>
#define MAX 20
using namespace std;

int main()
{
   int vetor[MAX];
   int n, valor, soma = 0;

   cout << "Digite quantos numeros: ";

   cin >> n;

    cout << "Digite os valores: ";

   for(int i = 0;i < n ;i++){
       cin >> vetor[i];

   }
    cout << "Digite o numero a ser comparado: ";

   cin >> valor;

   for(int i = 0 ;i < n ; i ++){
        for(int j = 0;j < n ;j++){
            if(vetor[i] + vetor[j] == valor){
                soma = soma + 1;
            }

        }
   }
   if(soma == 0){
       cout << "Não tem dois elementos que somam " << valor << endl;
   }else{
       cout << "Tem dois elementos que somam " << valor << endl;
   }
    return 0;
}

//Codigo com correções aplicadas após a avaliação ao qual faltou apenas um for para pegar os
//valores
//CODIGO JÀ CORRIGIDO

```



# Exemplo 3

```C++
//Concatenando dois vetores


#include <iostream>
#define MAX 5

using	namespace std;

int main()
{

	int tam, v1[MAX], v2[MAX], cont = 0;

	cin >> tam;

	//leitura do vetor1
	for(int i = 0;i < tam;i++){
		cin >> v1[i];
	}

	//leitura do vetor2
	for(int i = 0;i < tam;i++){
		cin >> v2[i];
	}

	//concatenamento

	const int x = tam * 2;

	int v3[x];

	for(int i = 0;i < x;i++){
		if(i < tam){
			v3[i] = v1[i];
		}else{
			v3[i] = v2[cont];
			cont++;
		}
   }

	//imprimindo o resultado
	for(int i = 0;i < x;i++){
		cout << "[" << v3[i] << "]";
	}

	cout << endl;

	return 0;

```
# Aula 13

# Revisão: Funções, Vetores e Matrizes

**Funções e Vetores**

**Crie um programa que lê a apartir do teclado n valores reais em um vetor.**
**O programa deverá calcular e mostrar a soma destes valores.Todas as operações relacionadas ao vetor deverão ser realizadas por meio de funções.**


```C++

#include <iostream>
#define MAX 100

using namespace std;

//função para ler os valores do vetor,OBS: todos os vetores são passados por referencia.
void lerValores(float v[MAX], int &n);
//Função para exibir os valores do vetor
void imprimirValores(float v[MAX], int n);
//função para somar os elementos
float somaElementos(float v[MAX], int n);

int main()
{
    float vetor[MAX], resultado;

    int qtd;

    lerValores(vetor, qtd);
    imprimirValores(vetor, qtd);
    resultado = somaElementos(vetor, qtd);

    cout << "Somatorio = " << resultado << endl;

    return 0;
}
void lerValores(float v[MAX], int &n){
    cout << "Informe a quantidade de Valores: ";
    cin >> n;

    cout << "Informe os Valores: ";

    for(int i = 0;i < n;i++){
    	cin >> v[i];
    }
}

void imprimirValores(float v[MAX], int n){
    cout << "Vetor: ";

    for(int i = 0;i < n;i++){
    	cout << v[i] << " ";
    }
    cout << endl;

}

float somaElementos(float v[MAX], int n){
    float soma = 0;

for(int i = 0;i < n;i++){
	soma = soma + v[i];
}

return soma;
}

```




**Maior elemento da matriz**

**Crie uma função que retorna a soma dos elementos de uma matriz com dimensão mxn;**


```C++
#include <iostream>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int somarElementos(int a[MAX_L][MAX_C], int m, int n);

int main()
{
    int matriz[MAX_L][MAX_C], m, n, soma;

    cout << "Informe as dimensões da matriz: ";
    cin >> m >> n;

    cout <<"Informe os valores da matriz: ";

    for(int i = 0;i < m;i++){
    	for(int j = 0;j < n;j++){
    		cin >> matriz[i][j];
    	}
    }
    soma = somarElementos(matriz,m ,n);

cout << "Soma dos elementos: " << soma << endl;

    return 0;
}

int somarElementos(int a[MAX_L][MAX_C], int m, int n){
int soma = 0;
    for(int i = 0;i < m;i++){
    	for(int j = 0;j < n;j++){
    		soma = soma + a[i][j];
    	}
    }
	return soma;
}

```

# Exemplo 

```
Implemente uma função que recebe duas palavras, s1 e s2, sem espaços, e retorna quantos caracteres de s1 aparecem em s2. Assuma que cada palavra possui no máximo 10 caracteres. Você deve imprimir na main o resultado dessa função.
Exemplos:
Se s1 = "bola" e s2 = "boi", o resultado da função deve ser 2, pois o primeiro e o segundo caracteres de s1
parecem em s2.
Se s1 = "banana" e s2 = "bonde", o resultado da função deve ser 3, pois o primeiro, o tercerio e o quinto
caracteres de s1 aparecem em s2.

Exemplo de entrada: bola biobio

Exemplo de saída: 2
```

```C++
#include <iostream>
#define MAX 50
#include <cstring>
using namespace std;

bool procuraChar(char p1[], char ch){
int tam1 = strlen(p1);
for(int i = 0;i < tam1;i++){
	if(p1[i] == ch){
		return true;
	}
}
return false;
}

int iguais(char s1[], char s2[]){
    int tam1 = strlen(s1);
    int tam2 = strlen(s2);
    int cont = 0;
    for(int i = 0;i < tam1;i++){
    	char ch = s1[i];
    	if(procuraChar(s2,ch)){
    		cont++;
    	}
}
return cont;
    return 0;
}

int main()
{
    char f1[MAX];
    char f2[MAX];

    cin >> f1 >> f2;

    cout << iguais(f1, f2) << endl;

    return 0;
}

```

# Exemplo 2 


```C++
//Verificar se uma matriz é ordenada

#include <iostream>
using namespace std;
const int MAX_L = 30;
const int MAX_C = 30;

void leMatriz (int matriz[][MAX_C], int linha, int coluna) {
    for (int i = 0; i < linha; i++) {
        for (int j = 0; j < coluna; j++) {
            cin >> matriz[i][j];
        }
    }
}

void imprimeMatriz (int matriz[][MAX_C], int linha, int coluna) {
    for (int i = 0; i < linha; i++) {
        for (int j = 0; j < coluna; j++) {
            cout << matriz[i][j] << " ";
        }
        cout << endl;
    }
}

bool vetorOrdenado (int v[], int n) {
    for (int i = 0; i < n - 1; i++) {
        if (v[i] > v[i + 1])
            return false;
    }

    return true;
}

int main()
{
    int matriz[MAX_L][MAX_C];
    int linha, coluna;
    cin >> linha >> coluna;

    leMatriz(matriz, linha, coluna);
    imprimeMatriz(matriz, linha, coluna);

    bool ordenada = true;
    for (int i = 0; i < linha; i++) {
        if (vetorOrdenado(matriz[i], coluna) == false) {
            ordenada = false;
            break;
        }
        if (i > 0 && matriz[i][0] < matriz[i-1][coluna-1]) {
            ordenada = false;
            break;
        }
    }

    if (ordenada)
        cout << "Igual ou crescente" << endl;
    else
        cout << "Nao ordenada" << endl;

    return 0;
}
```

# Exemplo 3 


```

Escreva uma função procuraVetor que recebe uma matriz m, o número de linhas l <= 30 e colunas c <= 30 de m,
um vetor v e o número n <= 30 de elementos de v. A função procuraVetor deve retornar verdadeiro caso o vetor
v seja igual a alguma linha de m, e falso caso contrário.Para ler a entrada, você deve primeiro ler o número
de linhas e colunas da matriz m, depois os elementos de m, depois o número de elementos do vetor v, e finalmente
os elementos de v.
Exemplo 1 (siga a formatação abaixo):
Entrada:

3 3
1 2 3
4 5 6
7 8 9
3
4 5 6

Saída: Achou vetor

Exemplo 2:
Entrada:

2 3
1 2 3
4 5 6
2
4 5

Saída:
Não achou vetor.
Entrada	Saída obtida	
Saída esperada
2 3
1 2 3
4 5 6
2
4 5	Achou vetor	Não achou vetor
2 2
1 2
3 4
2
1 3	Achou vetor	Não achou vetor
2 3
1 2 3
4 5 6
3
6 6 6	Achou vetor	Não achou vetor
1
```



```C++

#include <iostream>
#define MAX 30
#define MAX_L 30
#define MAX_C 30

using namespace std;

int procuraVetor(int m[][MAX_C],int l,int c, int v[MAX],int n){
 if(n != c){
	return false;
}
for(int i = 0 ;i < l;i++){
    bool achou = false;
for(int j = 0;j < c;j++){
	if(m[i][j] != v[j]){
		achou = false;
	}
	if(achou = true){
	 return true;
 	}
}
return false;
}
}

int main()
{
        int m[MAX_L][MAX_C];
        int v[MAX];
        int l ,c , n;
        bool resultado;
        cout << "Digite a quantidade de linhas e colunas: ";
        cin >> l >> c;

        cout << "Digite os valores da matriz: ";
        for (int i = 0; i < l; i++) {
            for (int j = 0; j < c; j++) {
                cin >> m[i][j];
            }
        }

        cout << "Digite o tamanho do vetor: ";
        cin >> n;

        for(int i = 0;i < n;i++){
            cin >> v[i];
        }

        resultado = procuraVetor(m,l,c,v,n);

        if(resultado == true){
            cout << "Achou vetor"<< endl;
        }else{
            cout << "Não achou vetor" << endl;
        }
    return 0;
}

```

```C++
//4
//1 2 3 4
//3
//4 1 9
#include <iostream>

using namespace std;

const int MAX = 10;
void leVetor(int v[], int n){
	for (int i = 0; i < n; i++) {
	       cin >> v[i];
	}
}
void rotaciona(int v1[], int n1){
	int aux[MAX];
	for(int i = 1; i < n1; i++){
		aux[i] = v1[i - 1];
	}
	aux[0] = v1[n1 - 1];
	for (int i = 0; i < n1; i++){
	   v1[i] = aux[i];
	}

int main (){
	int v1[MAX];
	int n1;    cin >> n1;
	leVetor(v1, n1);
	rotaciona(v1, n1);

	for(int i = 0; i < n1; i++){
	      	cout << v1[i] << " ";
		cout << endl;
	}

	return 0;
}

```


# Exemplo 4 

```
Embaralhando palavrasEscreva uma função para embaralhar uma string s1 com uma
string s2 e colocar o resultado em uma string s3.
```



```C++
#include <iostream>
#include <cstring>

using namespace std;

const int MAX = 31;
void embaralhar(char s1[], char s2[], char s3[]){
    int tam1 = strlen(s1);
    int tam2 = strlen(s2);
    int i1 = 0, i2 = 0, i3 = 0;

    while(i3 < tam1 + tam2){
	if(i2 == tam2 || (i1 < tam1 && i3 % 2 == 0)){// se o i for par
		s3[i3] = s1[i1];
		i1++;
	}else if(i1 == tam1 || ( i2 < tam2 && i3 % 2 == 1)){
		s3[i3] = s2[i2];
		i2++;
	}
	i3++;
    }
    s3[tam1 + tam2] = '\\0';
}

int main()
{
    char palavra1[MAX], palavra2[MAX];

    cin >> palavra1 >> palavra2;

    char palavra3[2*MAX];
    embaralhar(palavra1, palavra2,palavra3);

   cout << palavra1 << " + "<< palavra2 << " = "<< palavra3 << endl;
    return 0;
}
//Correção da questao acima

```



# Exemplo 5 

```
PalíndromoUm palíndromo é uma palavra que se pode ler, indiferentemente,
da esquerda para a direita ou vice-versa. Faça um programa que lê uma
palavra e imprime na tela se essa palavra é um palíndromo.
```

```C++
#include <iostream>
#include <cstring>
#define MAX 30
using namespace std;

bool palindromo(char palavra[MAX]){
    char copia[MAX];
    bool achou = false;
    int i, tam, iguais = 0;

    tam = strlen(palavra);

    for(i = 0;i < strlen(palavra);i++){
    	copia[i] = palavra[tam - 1];
    	tam--;
    }

    copia[i] = '\\0';
    tam = strlen(palavra);

    cout << "Palavra Original: " << palavra << endl;
    cout << "Palavra Copia: " << copia << endl;
    cout << endl;

    for(i = 0; i < tam;i++){
    	if(palavra[i] == copia[i]){
    		iguais++;
    	}
    }

    if(tam == iguais){
    	achou = true;
    }else{
    	achou = false;
    }
}

int main(){
    char palavra[MAX];
    bool result;
    cout << "Digite a palavra: ";
    cin.getline(palavra,MAX);

    palindromo(palavra);

    if(palindromo){
        cout << "\\"" << palavra << "\\""   << " é um palíndromo" << endl;
    }else{
        cout << "\\"" << palavra << "\\"" << " não é um palíndromo" << endl;
    }

	return 0;
}

```


# Exemplo 6 

```
(Função para calcular a diferença entre conjuntos) - Implemente uma função que receba
como parâmetros de entrada dois vetores de números inteiros e os seus respectivos tamanhos
(os vetores podem ter tamanhos diferentes). A função deve retornar na saída, a quantidade de
elementos que se repetem do vetor A no vetor B. Caso não possua elementos repetidos, deve-se
informar, "Sem elementos" conforme o exemplo. Os vetores possuem no máximo 10 elementos.
Obs: A sequência de leitura é tamanho do primeiro vetor, elementos do primeiro vetor,
tamanho do segundo vetor e elementos do segundo vetor. Considere que não existem elementos
repetidos no mesmo vetor. Veja o exemplo:
4  1 2 3 4
3  4 1 9
```

```C++
#include <iostream>
#define MAX 10

using namespace std;

void compare(int vetor1[MAX], int vetor2[MAX],int t1,int t2){
    int cont = 0;

    cout << "Tamanho de v1: ";
    cin >> t1;

    cout << "Insira os valores do v1: ";

    for(int i = 0;i < t1;i++){
        cin >> vetor1[i];
    }

    cout << "Tamanho de v2: ";
    cin >> t2;

    cout << "Insira os valores do v2: ";
    for(int j = 0;j < t2;j++){
        cin >> vetor2[j];
    }

    //verificar se a valores repetidos;
    for(int i = 0;i < t1;i++){
        for(int j = 0;j < t2;j++){
        if(vetor1[i] == vetor2[j]){
            cont++;
        }
    }
    }
    if(cont == 0){
        cout << "Sem elementos" << endl;
    }else{
        cout << cont << " Elementos" << endl;
    }
}

int main(){
    int v1[MAX], v2[MAX], t1 , t2;

    compare(v1, v2, t1, t2);

    return 0;
}

```

# Exemplo 7

```
(Função para informar se matriz é esparsa ) - Implemente funções para auxilar na
leitura dos dados de uma matriz e verificação se ela é esparsa, considerando o
número de linhas e colunas (<10). A função que testa se a matriz é esparsa deve
retornar verdadeiro caso a matriz seja esparsa, ou falso caso contrário. Considere
uma matriz esparsa quando ela possuir mais do que 70% dos seus elementos iguais a 0.
Veja o exemplo:
2  2

1  0     = > 	A matriz é esparsa
0  0
```

```C++
#include <iostream>
#define MAX_L 10
#define MAX_C 10

using namespace std;

bool esparsa(int m1[][MAX_C], int linha, int coluna){
   bool achou = false;
   int cont = 0, cont1 = 0;
   int tam = linha + coluna;
       for (int i = 0; i < linha; i++) {
        for (int j = 0; j < coluna; j++) {
            if(m1[i][j] == 0){
                cont++;
            }
            if(m1[i][j] == 1){
                cont1++;
            }
        }
    }
    if(cont1 < cont){
        achou = true;
    }else if(cont1 == cont){
        achou = false;
    }else{
        achou = false;
    }

    cout << "ACHOU: " << achou << endl;
    return achou;
}

int main(){
    int m1[MAX_L][MAX_C];
    int linha, coluna;
    bool result;
    cout << "Digite o valor das linhas e colunas: ";
    cin >> linha >> coluna;

    cout << "Digite os valores da Matriz: ";
    for (int i = 0; i < linha; i++) {
        for (int j = 0; j < coluna; j++) {
            cin >> m1[i][j];
        }
    }

    result = esparsa(m1,linha,coluna);

    if(result){
        cout <<"A matriz é esparsa" << endl;
    }else{
        cout << "A matriz não é esparsa" << endl;
    }

    return 0;
}

```

# Exemplo 8 

```
Escreva um programa que lê o número de elementos 1 <= n1, n2 <= 10 de dois vetores,
lê os n1 elementos do primeiro vetor, depois os n2 elementos do segundo vetor, e
determina os elementos em comum entre esses dois vetores, sem repetições.
Para isso, escreva uma função intersecao que recebe como parâmetros de entrada dois
vetores de número inteiros, v1 e v2, e a respectiva quantidade de elementos de cada um,
e como parâmetro de saída um vetor de inteiros v3. A função intersecao deve guardar no
vetor v3 os elementos que v1 e v2 possuem em comum, sem colocar elementos duplicados em
v3, e retornar a quantidade de elementos de v3. Após a função intersecao retornar, o
seu programa deve imprimir os elementos comuns a v1 e v2. Caso v1 e v2 não possuam
elementos em comum, imprima a mensagem Nenhum elemento igual
O seu programa deve ter pelo menos uma função auxiliar além da função intersecao.
A ordem em que os elementos são impressos não será levada em conta na correção do
professor (o Multiprova vai exigir uma determinada ordem).
```

```C++
#include <iostream>
#define MAX 10

using namespace std;
int lerValores(int v1[MAX], int v2[MAX],int &n1,int &n2){
    cout << "Digite o tamando de v1 e v2: ";
    cin >> n1 >> n2;

    cout << "Digite os valores do v1:" ;
    for(int i = 0;i < n1;i++){
        cin >> v1[i];
    }

    cout << "Digite os valores do v2:" ;
    for(int j = 0;j < n2;j++){
        cin >> v2[j];
    }

}
void imprimirValores(int v1[MAX],int v2[MAX],int n1,int n2){
    for(int i = 0;i < n1;i++){
    	cout  << "Vetor1: " << v1[i] << " " << " Vetor2: " << v2[i] << endl;
    }

}

void intersecao(int v1[MAX],int v2[MAX],int n1,int n2){
   int tam = 0, v3[MAX], valor = 0, cont = 0 ;

 for(int i = 0;i < n1;i++){
    for(int j = 0;j < n2;j++){
        if(v1[i] == v2[j]){
                v3[i] = v1[i];
                cont++;
            valor = v2[i];
            cout << "Contador: " << cont << endl;
        }
    }
}

    if(cont == 0){
        cout << "Nenhum elemento igual" << endl;
    }else{
    for(int i= 0;i < cont ;i++){
      cout << v3[i] << " ";
      }cout << endl;

    }

}

int main()
{
    int v1[MAX], v2[MAX] , n1 , n2, result;

    lerValores(v1, v2, n1, n2);
    imprimirValores(v1, v2, n1, n2);
    intersecao(v1, v2, n1, n2);

    return 0;
}

//precisa ser corrigida ainda

```

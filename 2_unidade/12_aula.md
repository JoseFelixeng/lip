# Aula 12 - Matrizes

Como declarar um array bidimensional(Matriz):

<tipo_elemento> <nome_array> [<numero_linhas>][<numero_colunas>];

# Exemplo 1 

```C++


//array bidimensional de inteiros
int m[2][3];

//array bidimensional de números
//de ponto flutuante

float r[10][10];

//array bidimensional de caracteres

char z[1000][1000];
Uma matriz pode ser interpretada como uma cadeia de vetores.

//Somando Matrizes
//Calcule C = A+B, sendo A e B duas matrizes quadradas com dimensão nxn.


#include <iostream>
#define MAX_L 50
#define MAX_C 50

using namespace std;

int main(){



int A[MAX_L][MAX_C];
int B[MAX_L][MAX_C];
int C[MAX_L][MAX_C];
int n;

cout << "Informe a dimensão das matrizes: ";
cin >> n;

//for usado para gerar todos os indices de linha
//A primeira matriz a receber valores será a matriz A

cout << "Informe os valores de A: " << endl;

for(int i = 0 ;i < n;i++){
//for usado para gerar todas as colunas;
	for(int j = 0;j < n;j++){
		//combinação de i,j para todas as combinações possiveis
		cin >> A[i][j];
	}

}
//Da mesma forma será usado  para gerar os elementos de B.

cout << "Informe os valores de B: " << endl;

for(int i = 0 ;i < n;i++){
//for usado para gerar todas as colunas;
for(int j = 0;j < n;j++){
//combinação de i,j para todas as combinações possiveis
cin >> B[i][j];
}
}

//usado para somar as duas matrizes
for(int i = 0;i < n;i++){
for(int j = 0;j < n;j++){
C[i][j] = A[i][j] + B[i][j];
}

}

cout << "Matriz C: " << endl;

//para imprimir uma matriz é preciso imprimir todos os valore 1 a 1.

for(int i = 0;i < n ;i++){
for(int j = 0;j < n ;j++){
cout << C[i][j] << " ";
}
//usado para imprimir as linhas separadas de forma matricial
cout << endl;
}
return 0;
}
```

# Exemplo 2 
```
Calculando o traço de uma matriz

# Traço da matriz

=>Dada uma matriz Anxn, calcule seu traço:
tr(A)=Somatorio(i = 1, n)a(ixi)
```



```C++
#include <iostream>
#define MAX_L 3
#define MAX_C 3

using namespace std;

int main(){

int A[MAX_L][MAX_C]={{1, 2, 3},
{4, 5, 6},
{7, 8, 9}};

const int n = 3;

// calculando o somatorio;

int traco = 0;

// diagonal principal i = j;

for(int i = 0;i < n;i++){
    for(int j = 0;j < n;j++){
        //i,j
        if(i == j){
        traco = traco + A[i][j];
	}
}

}

int diagonalS = 0;

for(int i = 0;i < n;i++){
    for(int j = 0;j < n;j++){
        //i,j
        if(n - 1 == i + j ){
        diagonalS = diagonalS + A[i][j];
	}
}

}

//O traço é a diagonal principal
cout << "Traco e = " << traco << endl;
cout << "A diagonal Secundaria e = " << diagonalS << endl;

return 0;

// codigo que identifica a diagonal primaria e secundaria de uma matriz
}

```



# Exemplo 3 

**Representando uma lista de nomes com matrizes**

```C++
#include <iostream>
#include <cstring>
#define MAX_N 100
#define MAX_NOME 50

using namespace std;

int main(){

char nomes[MAX_N][MAX_NOME];
int n, linhaMaior = 0;

cout << "Informe a quantidade de nomes: ";
cin >> n;

//para evitar que o enter usado em 'n' deixe de inserir um valor no nome

cout << "Digite  o nome: ";

//for usado para lê uma lista com n nomes proprios.

cin.ignore();
for(int i = 0;i < n;i++){
cin.getline(nomes[i], MAX_NOME);
}

linhaMaior = 0;

//for usado para encontrar o valor do indice maior caso seja maior que a primeira linha

for(int i = 1; i < n;i++){
if(strlen(nomes[i]) > strlen(nomes[linhaMaior])){
linhaMaior = i;
}

}

cout << "Maior nome: " << nomes[linhaMaior] << endl;
return 0;
}

```

# Exemplo 4

```
Faca um programa que, dados os números n, m (n,m <=30), lê do usuário os valores
de uma matriz A de inteiros de dimensão n x m. Depois, o programa deve ler um número
x e imprimir uma mensagem indicando se a matriz possui algum elemento cujo valor é x.
exemplo:
Linha  Coluna
3 		2

Valores
10  9
0  65
33  84

numero a ser se existe na matriz => 33;
```

```C++
#include <iostream>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int main(){
	int matriz[MAX_L][MAX_C];
	int n, m, x;
	bool achou = false;
	
	cout << "Digite a quantidade de linhas e colunas: ";
	cin >> n >> m;
	
	cout << "Digite os Valores: ";
	for(int i = 0;i < n;i++){ 	
		for(int j = 0;j < m;j++){
			cin >> matriz[i][j];
		}		
	}
	
	cout << "Digite o numero Buscado: ";
	cin >> x;
	
	for(int i = 0;i < n;i++){ 	
		for(int j = 0;j < m;j++){
			if(matriz[i][j] == x){
				achou = true;
		}
			
	}
	}	
	if(achou){
		cout << "Matriz tem elemento " << x << endl;
	}else{
		cout << "Matriz não tem elemento " << x << endl;
	}
	
	return 0;
}
```

# Exemplo 5 

```
Fac¸a um programa que, dados os números n, m (n,m <=30), lê do usuário os valores de 
uma matriz A de inteiros de dimensão n x m. Depois, o usuário vai digitar um caractere 
ch e um inteiro x. Caso ch seja igual 'l',o seu programa deve imprimir o maior elemento
na linha x de A. Caso ch seja igual a 'c',o seu programa deve imprimir o maior elemento
na coluna x de A.

exemplo1
3  2 (linha e coluna)
(Valores)
1  2 
3  4
5  6
(L ou C) indice
l  1 

```

```C++


#include <iostream>

using    namespace std;

const int MAXL = 30;
const int MAXC = 30;

int main()
{

int matriz[MAXL][MAXC];
int n, m;

cout << "Digite a quantidade de Linhas e colunas: ";
cin >> n >> m;

cout << "Digite os valores: ";

for(int i = 0;i < n;i++){
    for(int j = 0;j < m;j++){
        cin >> matriz[i][j];
    }
}

char ch;
int indice;

cout << "Digite o caracter e o indice: ";
cin >> ch >> indice;

if(ch == 'l'){
//percorrer todas as colunas da linha indice e ve qual é o maior elemento
int maiorLinha = matriz[indice][0];
for(int j = 1; j < m;j++){
    if(matriz[indice][j] > maiorLinha){
        maiorLinha = matriz[indice][j];
        
    }
}    
cout << maiorLinha << endl;
}else{
    //percorrer todas as LInhas e verificar o maior elemento da coluna
int maiorColuna = matriz[0][indice];
for(int i = 1;i < n;i++){
    if(matriz[i][indice] > maiorColuna){
        maiorColuna = matriz[i][indice];
    }
}
cout << maiorColuna << endl; 
}

    return 0;
}
```

# Exemplo 6 

```
Valores da MatrizFaça um programa que, dados os números n, m (n,m <=30), lê do usuário o
s valores de uma matriz A de inteiros de dimensão n x m. Depois, o programa deve imprimir
o menor elemento, o maior elemento e a média (com 2 casas decimais) dos valores da matriz.
```

```C++
#include <iostream>
#include <iomanip>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int main()
{
    int n,m;

int matriz[MAX_L][MAX_C];
int valorMe;
int valorMa;

cout << "Entre com valores para linhas e colunas: ";
cin >> n >> m;

for(int i = 0;i < n;i++){
	for(int j = 0;j < m;j++){
		cin >> matriz[i][j];
	}
}

valorMe = matriz[0][0];
valorMa = matriz[1][1];

for(int i = 0;i < n;i++){
	for(int j = 0;j < m;j++){
		if(matriz[i][j] < valorMe){
			valorMe = matriz[i][j];
		}
		if(matriz[i][j] > valorMe){
			valorMa = matriz[i][j];
		}
	}
}

cout << "Menor valor: "<< valorMe << endl;
cout << "Maior valor " << valorMa << endl;

int media = 0;

for(int i = 0;i < n;i++){
	for(int j = 0;j < m;j++){
		media = media +  matriz[i][j];
	}
}

cout << fixed << setprecision(2) << "Média dos valores: " << media/(n*m) << endl;

 

    return 0;
}
```

# Exemplo 7 


**Valores da Matriz: Faça um programa que, dados os números n, m (n,m <=30), lê do usuário os valores de uma matriz A de inteiros de dimensão n x m. Depois, o programa deve imprimir o menor elemento, o maior elemento e a média (com 2 casas decimais) dos valores da matriz.**

```C++

#include <iostream>
#include <iomanip>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int main()
{
    int n,m;
    int A[MAX_L][MAX_C];
    int menor = 0, maior = 0;
    float media = 0, cont = 0, soma = 0;
    
    cin >> n >> m;
    
    for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            cin >> A[i][j];
            cont++;
        }   
    }
    
    for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            soma = soma + A[i][j];
        }   
    }
    
    
    menor = A[0][0];
    maior = A[0][0];
    
       for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            if(A[i][j] < menor){
                menor = A[i][j];
            }
        }   
    }
           for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            if(A[i][j] > maior){
                maior = A[i][j];
            }
        }   
    }
    
    media = soma/cont;
    
    cout << "Menor valor: " << menor << endl;
    cout << "Maior valor: " << maior << endl;
     cout << "Média dos valores: "<< fixed << setprecision(2)  << media << endl;
    
    return 0;
}

```

# Exemplo 8

**Valores da Matriz: Faça um programa que, dados os números n, m (n,m <=30), lê do usuário os valores de uma matriz A de inteiros de dimensão n x m. Depois, o programa deve imprimir o menor elemento, o maior elemento e a média (com 2 casas decimais) dos valores da matriz.**

```C++
#include <iostream>
#include <iomanip>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int main()
{
    int n,m;
    int A[MAX_L][MAX_C];
    int menor = 0, maior = 0;
    float media = 0, cont = 0, soma = 0;
    
    cin >> n >> m;
    
    for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            cin >> A[i][j];
            cont++;
        }   
    }
    
    for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            soma = soma + A[i][j];
        }   
    }
    
    
    menor = A[0][0];
    maior = A[0][0];
    
       for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            if(A[i][j] < menor){
                menor = A[i][j];
            }
        }   
    }
           for(int i = 0;i < n;i++){
        for(int j = 0;j < m;j++){
            if(A[i][j] > maior){
                maior = A[i][j];
            }
        }   
    }
    
    media = soma/cont;
    
    cout << "Menor valor: " << menor << endl;
    cout << "Maior valor: " << maior << endl;
     cout << "Média dos valores: "<< fixed << setprecision(2)  << media << endl;
    
    return 0;
}

```

# Exemplo 9

**Matriz identidade: Faça um programa que, dado um numero n (n <= 30 ), crie e imprima a matriz identidade de dimensao (n)**


```C++


#include <iostream>
#define MAX_L 100
#define MAX_C 100

using namespace std;

int
main ()
{

//dimensão da matriz;
int n ;

cout << "Dimensão da matriz: ";
cin >> n;

int matriz1[MAX_L][MAX_C];
int matriz2[MAX_L][MAX_C];

for(int i = 0;i < n;i++){
	for(int j = 0;j < n;j++){
		if(i == j){
			matriz1[i][j] = 1;
		}else{
			matriz1[i][j] = 0;
		}
	}
}

for(int i = 0;i < n;i++){
	for(int j = 0;j < n;j++){
		cout << matriz1[i][j] << " ";
	}
	cout << endl;
}

  return 0;
}

```

# Exemplo 10

**Faça um programa que, dado uma matriz M de dimensão n x m (n,m <= 30), determine se todos os elementos internos da matriz são estritamente menores que os elementos da borda da matriz.**


```C++
#include <iostream>
#define MAX_L 30
#define MAX_C 30

using namespace std;

void leMatriz (int ma[][MAX_C], int n, int m) {
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            cin >> ma[i][j];
        }
    }
}

int main()
{
    int ma[MAX_L][MAX_C], n, m;
    cin >> n >> m;

    //Leitura da matriz:
    leMatriz(ma, n, m);

    bool maior = false;

    int cont = 0;
    // n = 4,  i = 0, 1, 2, 3 => i < n
    for(int i = 1; i < n-1; i++)
    {
        for(int j = 1; j < m-1; j++)
        {
            //Verifica elementos da primeira e última linha:
            for (int k = 0; k < m; k++) {
                if (ma[i][j] >= ma[0][k] || ma[i][j] >= ma[n-1][k]) {
                       maior = true;
                }
            }

            //Verifica elementos da primeira e última coluna:
            for (int k = 0; k < n; k++) {
                if (ma[i][j] >= ma[k][0] || ma[i][j] >= ma[k][m-1]) {
                       maior = true;
                }
            }

        }
    }

    if(maior == false)
    {
        cout << "Todos os elementos da borda são maiores que os elementos internos" << endl;
    }
    else
    {
        cout << "Nem todos os elementos da borda são maiores que os elementos internos" << endl;
    }

    return 0;
}

```

# Exemplo 11
```
E L L E L L L
L L E L L L E
T T T L L E L
```

```C++ 

#include <iostream>
using namespace std;

const int MAX_L = 3;
const int MAX_C = 7;

int main(){
    char matriz[MAX_L][MAX_C];
    int n = MAX_L;
    int m = MAX_C;

    for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            cin >> matriz[i][j];
        }
    }

    int contador = 0;
    for(int j = 0; j < m; j++) {

        bool estudou = false;
        for(int i = 0; i < n; i++) {
            if (matriz[i][j] == 'E') {
                estudou = true;
            }
        }

        if (!estudou) { //nao estudou em nenhum horario do dia j
            cout << j << endl;
        } else {
            contador++;
        }
    }

    if (contador == 7)
        cout << "João estuda todo dia" << endl;

    return 0;
}

```


# Exemplo 12


**Escreva um programa que recebe como entrada duas matrizes de números inteiros com mesmo tamanho (m x n). Seu objetivo deve ser realizar a
soma matricial elemento à elemento (element-wise), e exibir o resultado desta operação na saída. Por fim, indique qual foi o elemento de maior soma. Note que sua entrada deve obedecer a seguinte nomeclatura, tamanho para linhas e colunas, depois, os referidos elementos das matrizes.**


```C++
#include <iostream>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int main()
{
	int matriz1[MAX_L][MAX_C];
	int matriz2[MAX_L][MAX_C];
	int mResultado[MAX_L][MAX_C];
	int m, n,maior = 0;

	cout << "Digite as linhas e colunas: ";
	cin >> m >> n;

	cout << "Matriz1: ";
   for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            cin >> matriz1[i][j];
        }
    }

    cout << "Matriz2: ";
   for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            cin >> matriz2[i][j];
        }
    }

      for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            mResultado[i][j] = matriz1[i][j] + matriz2[i][j];
            if(maior < mResultado[i][j]){
				maior = mResultado[i][j];
			}
        }
    }

	  for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            cout << mResultado[i][j] << " "; ;
        }

    } cout << "maior: " << maior << endl;

	return 0;
}

```

# Exemplo 13 

```
Escreva um programa que inicialmente deve fazer a leitura do número de linhas e
de colunas de uma matriz M, com tamanho n x m (n, m <=30). Depois, receba os valores
inteiros de entrada que devem compor a matriz M e verifique se a matriz possui todos
os elementos com o mesmo valor, está ordenada em ordem crescente ou não ordenada.
Para fins de impressão, você deve considerar apenas duas saídas:
1 - "Não ordenada";
2 - "Igual ou ordem crescente".
exemplo: [2 2] [1 2 3 4 ] = igual ou ordenada
		 [2 2] [1 0 1 0 ] = Desordenada
                
```


```C++
#include <iostream>
#define MAX_L 30
#define MAX_C 30

using namespace std;

int main()
{
	int M[MAX_L][MAX_C];
	int m, n, valor = 0;
	bool igual = false;
	bool cres = false;
	bool des = false;

	cin >> m >> n;

   for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            cin >> M[i][j];
        }
    }

   for(int i = 0; i < n; i++){
        for(int j = 0; j < m; j++){
            if(M[i][j] == valor){
                igual = true;
            }else if(M[i][j] > valor){
               cres = true;
            }else {
                des = true;
            }
            valor = M[i][j];
        }
    }

    if(igual){
        cout << "Igual ou ordem crescente" ;
    }else if(cres){
        cout << "Igual ou ordem crescente";
    }else if(des){
        cout << "Não ordenada";
    }

	return 0;
}

```
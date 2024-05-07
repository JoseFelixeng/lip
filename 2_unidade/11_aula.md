# Aula 11 

### Aula 11 - Strings

```
Cadeias de caracteres (strings)

=> vetor do tipo "char"; =>Caso especial;

=>Exemplos: Nome, Nome Completo, parágrafo, senha, Placa de carro

=> Tabela ASCII



```
# Links importantes

**[memcpy](https://www.cplusplus.com/reference/cstring/memcpy/)**

Copy block of memory (function )

**[memmove](https://www.cplusplus.com/reference/cstring/memmove/)**

Move block of memory (function )

**[strcpy](https://www.cplusplus.com/reference/cstring/strcpy/)**

Copy string (function )

**[strncpy](https://www.cplusplus.com/reference/cstring/strncpy/)**

Copy characters from string (function )

**Concatenation**:

**[strcat](https://www.cplusplus.com/reference/cstring/strcat/)**

Concatenate strings (function )

**[strncat](https://www.cplusplus.com/reference/cstring/strncat/)**

Append characters from string (function )

**Comparison** :

**[memcmp](https://www.cplusplus.com/reference/cstring/memcmp/)**

Compare two blocks of memory (function )

**[strcmp](https://www.cplusplus.com/reference/cstring/strcmp/)**

Compare two strings (function )

**[strcoll](https://www.cplusplus.com/reference/cstring/strcoll/)**

- ***Compare two strings using locale (function )

**[strncmp](https://www.cplusplus.com/reference/cstring/strncmp/)**

Compare characters of two strings (function )

**[strxfrm](https://www.cplusplus.com/reference/cstring/strxfrm/)**

Transform string using locale (function )

**Searching**:

**[memchr](https://www.cplusplus.com/reference/cstring/memchr/)**

- ***Locate character in block of memory (function )

**[strchr](https://www.cplusplus.com/reference/cstring/strchr/)**

Locate first occurrence of character in string (function )

**[strcspn](https://www.cplusplus.com/reference/cstring/strcspn/)**

Get span until character in string (function )

**[strpbrk](https://www.cplusplus.com/reference/cstring/strpbrk/)**

Locate characters in string (function )

**[strrchr](https://www.cplusplus.com/reference/cstring/strrchr/)**

Locate last occurrence of character in string (function )

**[strspn](https://www.cplusplus.com/reference/cstring/strspn/)**

Get span of character set in string (function )

**[strstr](https://www.cplusplus.com/reference/cstring/strstr/)**

Locate substring (function )

**[strtok](https://www.cplusplus.com/reference/cstring/strtok/)**

Split string into tokens (function )

**Other**:

**[memset](https://www.cplusplus.com/reference/cstring/memset/)**

Fill block of memory (function )

**[strerror](https://www.cplusplus.com/reference/cstring/strerror/)**

Get pointer to error message string (function )

**[strlen](https://www.cplusplus.com/reference/cstring/strlen/)**

Get string length (function )

Macros:

[NULL](https://www.cplusplus.com/reference/cstring/NULL/)Null pointer (macro )

### Types:

- [size_t](https://www.cplusplus.com/reference/cstring/size_t/)*Unsigned integral type (type)
```
```


# Exemplo 1

```
Exemplo:
Leia seu nome a partir do teclado e imprima na tela:

>> "Bom dia, <nome_lido>!";

Depois, melhore o código  para ler o nome sobrenome;

é necessario atribuir um tamanho maximo de caracteres
```

```C++

#include <iostream>
#define MAX_NOME 50

using namespace std;

int main(){
char nome[MAX_NOME];

//Pegar todos os caracteres digitados até o apertar
//do ENTER

cin >> nome;

cout << "Bom dia, " << nome << endl;
return 0;
}
```

Sempre que os dados capturados forem uma sequencia sem espaços o "cin" pode ser utilizado.

# Exemplo 2


```
Exemplo:
=> Leia seu nome a partir do teclado e imprima na tela:

> "Bom dia, <nome_lido>!";
=> Depois, melhore o código  para ler o nome sobrenome;

é necessario atribuir um tamanho maximo de caracteres
```


```C++


#include <iostream>
#define MAX_NOME 50

using namespace std;

int main()
{
char nome[MAX_NOME];

//Pegar todos os caracteres digitados até o apertar
//do ENTER
//cin com getline é usado para pegar os valores até chegar ao maximo ou até o ENTER

cin.getline(nome, MAX_NOME);

cout << "Bom dia, " << nome << " !" <<  endl;

return 0;
}

```


# Exemplo 3 

** Receba do usuário uma frase e altere seu contéudo para que as vogais sejam removidas. Imprima a frase resultante.**


#### Inicialização:

**=> char texto[] = "Este eh um texto para teste!";**





```C++

#include <iostream>
#include <cstring>
#define MAX_FRASE 200

using namespace std;

bool ehVogal(char c);

int main()
{
char frase[MAX_FRASE];

//Pegar todos os caracteres digitados até o apertar
//do ENTER
//cin com getline é usado para pegar os valores até chegar ao maximo ou até o ENTER

cout << "Informe uma frase: ";

cin.getline(frase, MAX_FRASE);

//verificando na frase para saber se a vogal
//strlen usado para percorrer o vetor e encontrar a ultima casa do vetor frase
for(int i = 0;i < strlen(frase);i++){
	if(ehVogal(frase[i]) == true){
	//Remove o elemeno i ;
	//Empurrando todos os elementos para a esquerda
	for(int j = i;j <= strlen(frase);j++){
		frase[j] = frase[j + 1];
		}
	}
}
cout << "A frase é: " << frase << endl;
return 0;
}

bool ehVogal(char c){
return(c=='a' || c=='e' || c=='i' || c=='o' || c=='u');
}
```

# Exemplo 4 

**Escreva um programa que lê os nomes de duas pessoas (que podem conter espaços), cada um em uma linha, e imprime o nome que possui mais letras. O nome de uma pessoa contém somente letras minúsculas, sem acentos, e espaços. Se os dois nomes possuírem a mesma quantidade de letras, imprima o nome da primeira pessoa. Assuma que cada nome possui no máximo 20 caracteres.**


```C++

#include <iostream>
#define MAX 20
#include <cstring>

using namespace std;

int main()
{
char n1[MAX], n2[MAX] ;
int teste;
cout << "Digite a primeira pessoa: ";

cin.getline(n1, MAX);

cout << "Digite a segunda pessoa: ";
cin.getline(n2, MAX);

teste = strcmp(n1, n2);

if(teste  == 0){
    cout << n1 << endl;
}else if(teste < 0){
    cout << n2 << endl;
}else {
    cout << n1 << endl;
}

return 0;
}

//codigo precisa ser melhorado ainda incompleto;//

```

# Exemplo 5

```C++

#include <iostream>
#include <cstring>

#define MAX_TXT 100

using namespace std;

int main(){
char c1[MAX_TXT], c2[MAX_TXT];

//copiando os conteudos de c2 para c1;

cout << "Digite uma palavra: ";

cin >> c2;

//Todos os indices do 0 até o 0/ no final do vetor c2 serão copiados para c1.

strcpy(c1, c2);

cout << "C1: " << c1 << endl;
```

# Exemplo 6

```C++

#include <iostream>
#include <cstring>

#define MAX_TXT 100

using namespace std;

int main(){
char c1[MAX_TXT], c2[MAX_TXT];

//copiando os conteudos de c2 para c1;

cout << "Digite uma palavra: ";

cin >> c2;

//Todos os indices do 0 até o 0/ no final do vetor c2 serão copiados para c1.

strcpy(c1, c2);

cout << "C1: " << c1 << endl;
return 0;
}

```

# Exemplo 7 

```C++
#include <iostream>
#include <cstring>

#define MAX_TXT 100

using namespace std;

int main(){
char c1[MAX_TXT], c2[MAX_TXT];

//copiando os conteudos de c2 para c1;

cout << "Digite uma palavra: ";

cin >> c1;

cout << "Digite uma palavra: ";

cin >> c2;

//O strcat faz com que os valores de entrada sejam concatenados dentro de c1

strcat(c1, c2);

cout << "C1: " << c1 << endl;
cout << "C2: " << c2 << endl;
return 0;
}
```

# Exemplo 8 

```C++
#include <iostream>
#include <cstring>

#define MAX_TXT 100

using namespace std;

int main(){
char c1[MAX_TXT], c2[MAX_TXT];

//copiando os conteudos de c2 para c1;

cout << "Digite uma palavra: ";

cin >> c1;

cout << "Digite uma palavra: ";

cin >> c2;

//O strcat faz com que os valores de entrada sejam concatenados dentro de c1
// para concatenar com espaços é necessario apenas que seja feita a concatenação de um dos vetores com espaço

strcat(c1, " ");
strcat(c1, c2);

cout << "C1: " << c1 << endl;
cout << "C2: " << c2 << endl;
return 0;
}
```

# Exemplo 9 

```C++
#include <iostream>
#include <cstring>

#define MAX_TXT 100

using namespace std;

int main(){
int resultado;
char c1[MAX_TXT], c2[MAX_TXT];

//copiando os conteudos de c2 para c1;

cout << "Digite uma palavra: ";

cin >> c1;

cout << "Digite uma palavra: ";

cin >> c2;

//comparando duas palavras para saber quem vem primeiro em ordem alfábetica

resultado = strcmp(c1, c2);

if(resultado == 0 ){
	cout << "Palavras Iguais: " << endl;
}else if(resultado < 0){
	cout << c1 << " " << c2 << endl;
}else {
	cout << c2 << " " << c1 << endl;
}
	return 0;
}
```

# Exemplo 10

**Substituir: Faça um programa que, dada uma string s e dois chars c1 e c2, substitui todas as ocorrência de c1 em s por c2 e vice-versa.**

```C++

#include <iostream>
#define MAX 101
#include <cstring>

using namespace std;

int main()
{
char v1[MAX],v2[MAX];
char l1, l2;
//cout << "Digite a frase para comparar: ";

cin.getline(v1, MAX);

//cout << "Letra a ser substituida: ";

cin >> l1;

//cout << "Letra a ser substituir: ";

cin >> l2;

for(int i = 0;i < strlen(v1);i++){
	v2[i] = v1[i];
}

v2[strlen(v1)] = 0;

for(int i = 0;i < strlen(v1);i++){
	if(v1[i] == l1){
			v1[i] = l2;

	}else if(v1[i] == l2){
	    v1[i] = l1;
	}
}

cout << v2 << " => " << endl;
cout << v1 << endl;
return 0;
}

```

# Exemplo 11

**PalíndromoUm palíndromo é uma palavra que se pode ler, indiferentemente, da esquerda para a direita ou vice-versa. Faça um programa que lê uma palavra e imprime na tela se essa palavra é um palíndromo.**


```C++
#include <iostream>
#include <cstring>
#define MAX 30
using namespace std;

int main(){

char  palavra[MAX], copia[MAX];
int i, tam, iguais = 0;

cout << "Digite a palavra: ";
cin >> palavra;

tam = strlen(palavra);

for(i = 0;i < strlen(palavra);i++){
copia[i] = palavra[tam - 1];
tam--;
}

copia[i] = '\0';
tam = strlen(palavra);

cout << "Palavra Original: " << palavra << endl;
cout << "Palavra Copia: " << copia << endl;

for(i = 0; i < tam;i++){
	if(palavra[i] == copia[i]){
		iguais++;
	}
}
	
if(tam == iguais){
	cout << palavra << " E palindromo" << endl;
}else{
	cout << palavra << " Não e palindromo " << endl;
}
	return 0;
}

```

# Exemplo 12

**É um número?Escreva um programa que, dada uma string, determine se a string representa ou não um número inteiro. Dica: utilize a biblioteca ctype.**


```C++
#include <iostream>
#include <cctype>
#include <cstring>
#define MAX 200

using namespace std;

int main(){
char inteiro[MAX];
int tamanho, cont = 0;
cin.getline(inteiro, MAX);
tamanho = strlen(inteiro);
for(int i = 0; i < tamanho; i++){
	if(inteiro[0] == '-'){
	    cont = 0;
	}else if(inteiro[i] >= 'a' && inteiro[i] <='z' || '-' == inteiro[i]){
        cont++;
    }
}
if(cont > 0){
    cout << inteiro << " não representa um número";
}
else {
	cout << inteiro << " representa um número";
}

return 0;
}

```

```C++ 
cout << "Informe a frase: ";

cin.getline(f1,MAX);

for(int i = 0;i < strlen(f1);i++){
	if(f1[i]=='a' || f1[i]=='e' || f1[i]=='i' || f1[i]=='o' || f1[i]=='u'){
		cont1++;
		cout << "Cont1: " << cont1 << endl;
	}else{
		cont2++;
		cout << "Cont2: " << cont2 << endl;
	}
}
if(cont1 == cont2){
	   cout << "Possui o mesmo número"	<< endl;
}else if(cont1 < cont2){
	cout << "Possui mais consoantes" << endl;
}else{
	cout << "Possui mais vogais" << endl;
}

return 0;
}

```

# Exemplo 13 

**Implemente um programa que deve ler na entrada duas (strings), com tamanho máximo de 20 caracteres. O objetivo é criar uma nova string que seja o resultado da concatenação das duas entradas. Isto sem utilizar a biblioteca <cstring>. Por fim,  imprimir na saída o resultado após a concatenação. Obs: Não deixe de "fechar" a string resultante com o '\0'. Veja o exemplo abaixo:**

```C++

#include <iostream>
#define MAX_menor 20
#define MAX_maior 50

using namespace std;

int main(){
char string1[MAX_menor];
char string2[MAX_menor];
char string3[MAX_maior]="";
```


# Exemplo 14

**MaiúsculasFaça um programa que lê uma string e imprime a primeira letra de cada palavra em maíuscula. Dica: utilize a função toupper da biblioteca ctype.**


```C++
#include <iostream>
#include <cstring>
#include <cctype>
#define MAX 100

using namespace std;

int main() {


char frase[MAX];
int i;

cin.getline(frase, MAX);

strlen(frase);

for (i = 0; i < strlen(frase) + 1; i++) {
    if (i == 0 || frase[i - 1] == ' ')
        frase[i] = toupper(frase[i]);
    else
        frase[i] = frase[i];
}



cout << frase << endl;


return 0;

}

```

# Exemplo 15 

**Escreve um programa que deve fazer a leitura de uma string apenas letras minúsculas) com tamanho máximo de 30 caracteres e sem espaços. Informar se esta string possui mais vogais, consoantes ou o mesmo número de vogais e consoantes em sua composição. Imprima na saída o resultado conforme o exemplo:**



```C++
#include <iostream>
#include <cstring>
#define MAX 100

using namespace std;

int main(){
char f1[MAX];
int cont1 = 0, cont2 = 0;
cout << "Digite a primeira frase: ";
cin.getline(string1, MAX_menor);
cout << "Essa e a string1: " << string1 << endl;

cout << "Digite a primeira frase: ";
cin.getline(string2, MAX_menor);
cout << "Essa e a string2: " << string2 << endl;

//guardando a primeira string

int i = 0;

while(string1[i] != '\\0'){
	string3[i] = string1[i];
	i++;
}

cout << "Vetor 3 apos ser preenchido pelo vetor 1: " << string3 << endl;

//guardando a primeira string

int j = 0;

while(string2[j] != '\\0'){
	string3[i] = string2[j];
	i++;
	j++;
}

cout << "Vetor 3 apos ser preenchido pelo vetor 2: " << string3 << endl;

 string3[i] = '\\0';

 cout << "OS VETORES CONCATENADOS FICAM DA SEGUINTE FORMA:" << string3 << endl;

return 0;

// código ajustado com debugs de acordo com a questão pedida
}
```
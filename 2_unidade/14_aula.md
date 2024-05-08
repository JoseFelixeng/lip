# Aula 14 - Resumo das aulas 


### Tipos Estruturados


### **Objetivo da aula**

Responder à seguinte pergunta:

Eu sei como:

- armazenar *uma* informação de um tipo (**variável**);
- armazenar *várias* informações do mesmo tipo *sob um mesmo nome* (**vetores/matrizes**)

> E se eu quiser armazenar informações de tipos diferentes sob um mesmo nome?



### **Motivação**

Muitas vezes precisamos agrupar informações de *tipos diferentes* sob um **mesmo nome**.

- *Aluno*: CPF, RG, nome, sobrenome, endereço, etc.
- *Disciplina*: Código, nome, créditos, ementa, etc.
- *Livro*: ISBN, título, ano, número de páginas, etc.


### **Motivação**


se eu quiser armazenar os dados dos estudantes da UFRN....

`char cpf[NUM_EST][TAM_MAX]; char nome[NUM_EST][TAM_MAX]; char email[NUM_EST][TAM_MAX]; int semestre[NUM_EXT];`

será uma boa solução ?



### **Tipos Estruturados ou Estruturas de Dados Heterogêneas**

Uma estrutura (*struct*) ou registro em C++ é uma coleção de um ou mais valores (possivelmente de *tipos diferentes*), agrupados sob um *único nome*.

As estruturas são um recurso importante para *organizar* os dados de um programa graças à possibilidade de tratar *um grupo de valores como uma única variável*.

---

### **Tipos Estruturados**

Uma estrutura é um *tipo* de dado cujo formato é *definido* pelo programador.

Vídeo Tipos estruturados: definição, declaração de variáveis e acesso aos campos (11.02)

---

https://www.youtube.com/embed/kh3Z2ywZJmI

### **Definição de tipos estruturados**

Elementos individuais de uma estrutura são chamados *membros*;

Os membros podem ter *tipos diferentes* (primitivo, matriz ou struct);

O nome de uma estrutura agrega vários membros, enquanto os membros, individualmente, devem possuir *identificadores únicos*

Definição

// Cada identificador define um membro.

```
struct Nome{
 tipo1 identificador1;
 ...
 tipon identificadorn;
 } ;

```

Armazenar uma data

```

struct Data {
  int dia;
  int mes;
  int ano;
} ;

```

```
struct contaBancaria{
 char Nome[15];
 char ContaNo[10];
 double saldo;
 Data abertura;
};

```

```
struct Estudante{
 char Nome[15];
 int Id;
 char Curso[20];
 char sexo;
};

```

Data é um tipo definido pelo usuário e podemos utilizar ele para definir outros tipos estruturados.
Declaração de variáveis do tipo `struct`**

`Estrutura Identificador;`

Exemplo:

`Estudante E1, E2 ;`

![[Pasted image 20240112152221.png]]
Acesso aos membros

Os membros de um tipo estruturado são acessados com a utilização do *operador ponto*(.):
`variavel.membro;`

Exemplo:

`Estudante E;
cin >> E.nome ;
cin >> [E.Id](http://e.id/);
cin >> E.Curso;
cin >> E.sexo;

if (E.sexo == 'M')
cout << "Sr. " << E.nome;
else
cout << "Sra. " << E.nome;`
Estruturas aninhadas

`struct Ponto{

```
   double x, y;
};
struct Linha{
   Ponto p1, p2;
};
struct Triangulo{
   Ponto p1, p2, p3;
};`

```

### Estruturas aninhadas

![[Pasted image 20240112152359.png]]

Como representamos essas figuras?

`Ponto vp = {4,11}; // Inicializando

```
Linha vl = { {2,7}, {10,9}} ;
Triangulo vt; // Declarar e depois atribuir
vt.p1.x = 2; vt.p1.y = 0;
vt.p2.x = 6; vt.p2.y = 5;
vt.p3.x = 8; vt.p3.y = 3;`

```

Vetor de estruturas

Um vetor de estruturas armazena em cada posição um tipo estruturado (com vários membros):
![[Pasted image 20240112152442.png]]

### **Vetor de estruturas**

`Estudante Turma[100];

```
strcpy(Turma[98].Nome, "Chan Tai Man");
Turma[98].Id = 12345;
strcpy(Turma[98].Curso, "COMP");
Turma[98].Sexo = 'M';
// Podemos utilizar o operador de atribuição!
Turma[0] = Turma[98];`

```

![[Pasted image 20240112152607.png]]

### Vetor como membro de estrutura

```
struct Quadrilatero{
  Ponto vertices[4];
};

int main(){
  Quadrilatero q;
	...
}

```

Vetor como membro de estrutura

![[Pasted image 20240112152703.png]]

```
Quadrilatero q1 = { { {4,1}, {4,3}, {10,3}, {10,1}} };
Quadrilatero q2;
q2.vertices[0].x = 4 ; q2.vertices[0].y = 1;
q2.vertices[1].x = 4 ; q2.vertices[1].y = 3;
q2.vertices[2].x = 10 ; q2.vertices[2].y = 3;
q2.vertices[3].x = 10 ; q2.vertices[3].y = 1;

```

Estruturas como parâmetros de funções

Parâmetros por valor:

```
struct Ponto{
   double x, y;
};

struct Quadrilatero{
  Ponto vertices[4];
};

void print_ponto(Ponto p){
 cout << "(" << p.x << "," << p.y << ")";
}

void print_quadrilatero(Quadrilatero q){
  int i;
  for(i=0;i < 4;i++){
    print_ponto(q.vertices[i]) ;
    cout << endl ;
  }
}

```

Estruturas como parâmetros de funções

Parâmetros por referência:

```
struct Ponto{
   double x, y;
};
struct Quadrilatero{
  Ponto vertices[4];
};

void ler_ponto(Ponto &p){
 cin >> p.x >> p.y;
}
void ler_quadrilatero(Quadrilatero &q){
    for(int i=0; i < 4 ; i++)
        ler_ponto(q[i]);
}

```

### Exemplo

Foi realizada uma pesquisa entre 100 habitantes de uma certa região. De cada habitante foram coletados os dados: CPF, idade, sexo, salário e número de filhos. Construa um programa C++ que armazene as informações da pesquisa e calcule a média do salário dos habitantes e de filhos e liste os habitantes com salário inferior a média e o número de filhos superior a média.

---

### Exemplo

Primeiro definimos a estrutura para armazenar os dados das pessoas:

```
struct Pessoa{
    char cpf[12];
    int idade;
    char sexo;
    float salario;
    int nfilhos;
};

```

---

### Exemplo

Podemos definir pelo menos 4 funções:

```
void ler(Pessoa &P); // ler as informações de uma pessoa
void imprimir(Pessoa P); // imprimir as informações de uma pessoa
float mediaSalarios(Pessoa vp[], int n); // calcular a média dos salários
float mediaFilhos(Pessoa vp[], int n); // calcular a média do número de filhos

```

---

### Exemplo

Implementar as funções

```
    cin >> P.cpf >> P.idade >>
    P.sexo >> P.salario >> P.nfilhos;
};

```

---

### Exemplo

Implementar as funções

```
void imprimir(Pessoa P){
    cout<< "CPF: "<< P.cpf << " idade: " << P.idade
        << " sexo: " << P.sexo << " salário: " << P.salario
        << " número de filhos: " << P.nfilhos << endl ;
};

```

---

### Exemplo

Implementar as funções

```
float mediaSalarios(Pessoa vp[], int n){
    float soma =0;
    for(int i=0 ; i < n ; i++){
        soma += vp[i].salario;
    }
    return soma / n ;
};

```

---

### Exemplo

Implementar as funções

```
float mediaFilhos(Pessoa vp[], int n){
    int soma =0;
    for(int i=0 ; i < n ; i++){
        soma += vp[i].nfilhos;
    }
    return (float) soma / n ;
};

```

---

### Exemplo

Agora sim, podemos implementar a função `main`:

```
int main(){
    Pessoa dados[TAM];
    int n;
    float msalario, mfilhos;
    cin >> n;

    // Ler os dados das n pessoas
    for(int i=0 ; i < n ; i++)
        ler(dados[i]);

    // calcular as médias
    msalario = mediaSalarios(dados, n);
    mfilhos = mediaFilhos(dados, n);
    cout << "Média Salário: " << msalario
        << " Média Número de Filhos: " << mfilhos << endl;

    // Imprimir as pessoas
    for(int i=0 ; i < n ; i++){
        if(dados[i].salario < msalario &&
           dados[i].nfilhos > mfilhos)
            imprimir(dados[i]);

    }
    return 0;
}

```

## Aula 02

---

### Distância entre pontos

Na última aula implementamos uma função para calcular a distância entre dois pontos:

```
struct Ponto {
	double x, y;
};

double dist (Ponto p1, Ponto p2) {
	return sqrt(pow(p2.x - p1.x, 2) +
                pow(p2.y - p1.y, 2));
}

```

---

### Distância entre pontos

## Como podemos calcular a distância em um "caminho" de pontos?

### Distância entre pontos

Representaremos o caminho como um vetor de pontos:

```
Ponto caminho[TAM];`

E definimos uma função com protótipo:
float distancia(Ponto vp[], int n);`

```

---

### Distância entre pontos

A função simplesmente calcula o somatório das distâncias:

```
float distancia(Ponto vp[], int n){
    float soma=0;
    for(int i = 0 ; i < n - 1 ; i++){
        soma += dist(vp[i], vp[i+1]);
    }
    return soma;
}

```

---

### Números Complexos

Como representamos um número complexo?

```
struct Complexo{
  double real;
  double img;
};

```

---

### Números Complexos

Agora podemos utilizar números complexos nos nossos programas:

```
Complexo c;    //Variável tipo Complexo
c.real = 3.4;  //Parte real
c.img = 12.2;  // Parte imaginária

```

---

### Números Complexos

Muito mais interessante, podemos definir diferentes funções utilizando números complexos.

```
void print(Complexo x){
  cout << x.real;
  if (x.img <0)
    cout << " - " ;
  else
    cout << " + " ;

  cout << x.img << "i" << endl;

```

---

### Números Complexos

Módulo de um complexo: $ Z = \sqrt{real^2 + img^2}$

```
double modulo(Complexo x){
  return sqrt(pow(x.real,2.0) +
              pow(x.img,2.0));
};

```

---

### Números Complexos

Quando 2 números complexos são iguais ?

- A parte real deve ser igual
- A parte imaginária deve ser igual

---

### Números Complexos

Quando 2 números complexos são iguais ?

- A parte real deve ser igual
- A parte imaginária deve ser igual

```
bool iguais(Complexo x, Complexo y){
  if(x.real == y.real && x.img == y.img)
    return true;
  else
    return false;
}

```

---

### Números Complexos

Soma de números complexos.

Qual deveria ser o protótipo da função?

---

### Números Complexos

Soma de números complexos.

```
Complexo soma(Complexo x, Complexo y){
  Complexo z;
  z.real = x.real + y.real;
  z.img = x.img + y.img;
  return z;
}

```

Note que a função **retorna** um número complexo.

---

### Números Complexos

O conjugado de $ Z = a + bi$ é

$\overline{Z} = a - bi$

---

### Números Complexos

O conjugado de $ Z = a + bi$ é

$\overline{Z} = a - bi$

```
Complexo conjugado(Complexo x){
  Complexo z;
  z.real = x.real;
  z.img = -1.0 * x.img;
  return z;

```

Novamente, a função **retorna** o resultado (um número complexo).

---

### Números Complexos

Um exemplo:

```
int main(void){
  Complexo c, d;
  c.real = 3.1;
  c.img = 5.4;
  d.real = 2.2;
  d.img = 7.0;

  cout << "Iguais: " << iguais(c,d) << endl;
  print(conjugado(c));
  cout << modulo(d) << endl;
  print(conjugado(soma(c,d)));
  return 0;
}

```

---

## Tipos de dados Enumerados

---

### Enumeração

*Enumeração*: Conjunto de constantes *inteiras* em que cada uma delas é representada por um nome

```
enum Mes {Jan, Fev, Mar, Abr, Mai, Jun, Jul, Ago, Set, Out, Nov, Dez};

int main(void){
  Mes m1, m2;
  m1 = Dez;
  m2 = Abr;
  cout << "m1=" << m1 << endl; // 11
  cout << "m2=" << m2 << endl; // 3
  return 0;
};

```

---

### Exemplo

```
enum ESexo {Feminino, Masculino};

// Struct e Enum:
struct Pessoa{
  char nome[50];
  ESexo sexo;
};

int main(){
    Pessoa P;
    strcpy(P.nome, "Maria");
    P.sexo = Feminino;
    ...
    return 0;
}

```

---

### Exemplo

Queremos filtrar uma lista de pessoas e selecionar só as mulheres.

- Entrada: Um vetor de pessoas (e seu número de elementos)
- Saída: Um vetor de pessoas

---

### Exemplo

Queremos filtrar uma lista de pessoas e selecionar só as mulheres.

```
// Retorna o número de elementos do vetor de saída
// Segundo vetor: saída da função
int filtrar(Pessoa vp[], int n, Pessoa vmulheres[]){
    int pos = 0; // índice para atribuir valores em vmulheres

    for( int i=0; i < n ; i++){
        if (vp[i].sexo == Feminino)
            vmulheres[vpos++] = vp[i];
    }
    return pos;

};

```

---

### Exemplo

Queremos filtrar uma lista de pessoas e selecionar só as mulheres.

```
    Pessoa dados[TAM], vm[TAM];
    ...
    int nm = filtrar(dados, n, vm);
    imprimir(vm, nm);
    ...
    return 0;
};

```

---

---

### Aula 03

---

### Exemplo Restaurante

Crie uma estrutura para descrever restaurantes com as informações a seguir:

- Nome
- Endereço
- Preço Medio
- Qualidade (pode ser Excelente, Bom ou Regular)
- Tipo de Comida (pode escolher entre internacional, regional, carnes, vegetariano)

---

### Exemplo Restaurante

Definimos duas enumerações e uma estrutura:

```
enum EQualidade {Excelente, Bom , Regular};
enum ETipo {Internacional, Regional, Carnes, Vegetariano};

struct Restaurante {
	char nome[50];
    char endereco[100];
    double preco;
    EQualidade qualidade;
    ETipo tipo;
};

```

---

### Exemplo Restaurante

Queremos determinar o restaurante mais barato.

Definimos várias funções auxiliares:

```
void ler(Restaurante &R){
    int tipo, qualidade;
    cout << "Nome: " ;
    cin.getline(R.nome, 50);
    cout << "Endereço: " ;
    cin.getline(R.endereco, 100);
    cout << "Preço médio: " ;
    cin >> R.preco;
    cout << "Qualidade: (0) para Excelente, (1) para bom e (2) para regular";
    cin >> qualidade ;
    R.qualidade = (EQualidade) qualidade;
    cout << "Tipo: (0) para Internacional, (1) para Regional e (2) para Carnes e (3) para Vegetariano";
    cin >> tipo ;
    R.tipo = (ETipo) tipo;
    cin.get();
};

```

---

### Exemplo Restaurante

Queremos determinar o restaurante mais barato.

Definimos várias funções auxiliares:

```
    cout <<" Nome: " << R.nome << endl;
    switch(R.tipo){
        case Internacional: cout << "Internacional" << endl; break;
        case Regional: cout << "Regional" << endl; break;
        case Carnes: cout << "Carnes" << endl; break;
        case Vegetariano: cout << "Vegetariano" << endl; break;
    }
    cout << " Preço médio:  " << R.preco << endl ;
};

```

---

### Exemplo Restaurante

Queremos determinar o restaurante mais barato.

```
    double pbaixo = vr[0].preco;
    int menor = 0;

    for(int  i=1 ; i < n ; i++){
        if (pbaixo > vr[i].preco){
            pbaixo = vr[i].preco;
            menor = i;
        }
    }
    return vr[menor];
}

```

Note que a função *retorna um restaurante*

---

### Exemplo Restaurante

Queremos determinar o restaurante mais barato.

```
int main () {
    int n;
    Restaurante vr[TAM];
    cout << "Número de restaurantes: " ;
    cin >> n;
    cin.get();

    for (int i = 0 ; i < n ; i++){
        ler(vr[i]);
    }

    Restaurante R = maisBarato(vr, n);
    cout << " O Restaurante mais barato é: " ;
    imprimir(R);

	return 0;
}

```

---

### Exemplo Restaurante

Como filtramos uma lista de restaurantes para selecionar só aqueles avaliados como Excelente?

```
int RExcelente(Restaurante vr[], int n, Restaurante resultado[]){
    int pos = 0 ;

    for(int  i=0 ; i < n ; i++){
        if (vr[i].qualidade == Excelente)
            resultado[pos++] = vr[i];
    }
    return pos;
}

```

- A função *retorna* o número de restaurantes Excelente
- O parâmetro `resultado` é utilizado para armazenar o **resultado**

---

### Exemplo Restaurante

Como filtramos uma lista de restaurantes para selecionar só aqueles avaliados como Excelente?

```
int main () {
    int n;
    Restaurante vr[TAM], vrex[TAM];
    cout << "Número de restaurantes: " ;
    cin >> n;
    cin.get();

    for (int i = 0 ; i < n ; i++){
        ler(vr[i]);
    }

    int nexc = RExcelente(vr,n, vrex);
    cout << "Lista dos restaurantes avaliados como Excelente: " << endl ;
    for (int i = 0 ; i < nexc ; i++){
        imprimir(vrex[i]);
        cout << "****" << endl ;
    }
	return 0;
}

```

---

### Listas

Em qualquer sistema precisamos armazenar vários dados do mesmo tipo. Por exemplo:

- Em uma turma temos 30 estudantes (ordenados alfabeticamente).
- Em um supermercado devemos armazenar a lista de todos os produtos disponíveis.
- Em uma empresa trabalham muitos funcionários.

> Quando utilizamos arrays, o número de elementos a serem armazenados é fixo.
> 

---

### Listas

Considere um sistema para armazenar os produtos de um supermercado. Neste caso, precisamos de uma **Lista** que é uma estrutura de dados que oferece as seguintes operações:

- Adicionar e remover elementos (produtos neste caso)
- Retornar o número de produtos na lista.
- Retornar o elemento em uma posição dada.

---

### Listas

Temos várias opções para implementar a Lista:

- Implementar a lista utilizando *arranjos*.
- Implementar a lista utilizando *listas encadeadas*.

Algumas restrições:

- A lista não permite remover elementos.
- Os elementos são inseridos sempre no final da lista.
- Vamos assumir que a lista tem uma capacidade máxima (fixa).

---

### Listas (Utilizando arranjos)

1. Definimos a estrutura *Produto*
2. Definimos a estrutura Lista (de produtos):
3. Implementamos algumas funções para manipular essas estruturas

---

### Listas

Começamos com produto:

```
struct Produto{
  int id;
  char nome[20];
};

```

---

### Listas

Função para *criar* um produto

```
Produto novo(int id, char nome[]){
  Produto P;
  P.id = id;
  strcpy(P.nome, nome);
  return P;
};

```

---

### Listas

Função para imprimir um produto

```
  cout << P.id << " " << P.nome;
}

```

---

### Listas

Definimos a lista:

```
  // TAM= capacidade máxima
  Produto vp[TAM];
  // n=número de elementos atualmente armazenados
  int n;
};

```

---

### Listas

Agora podemos definir várias funções para manipular a lista:

- Criar uma lista vazia
- Imprimir uma lista
- Testar se a lista está vazia
- Retornar o tamanho da lista
- Inserir um elemento no final da lista
- Retornar um elemento da lista

---

```
// Cirar uma lista vazia
Lista novaLista(){
 Lista L;
 L.n = 0;
 return L;
};

```

---

```
// Determinar o tamanho da lista
int tamanho(Lista L){
 return L.n;
}

```

---

## Imprimir

```
// Imprimir os elementos da lista
void imprimir(Lista L){
 for(int i=0 ; i < L.n ; i++){
   imprimir(L.vp[i]);
   cout << endl ;
 }
}

```

---

## Inserir

```
// Inserir um elemento no final da lista
bool inserir(Lista &L, Produto P){
  if (L.n == TAM)
    return false;
  L.vp[L.n] = P;
  L.n++;
  return true;
};

```

---

## Retornar um elemento

```
Produto elemento(Lista L, int i){
  if (i<0 || i>= L.n) // Posição não válida
    return L.vp[0];
  return L.vp[i];
};

```

---

## Um exemplo

```
int main(){
  Lista L = novaLista() ;
  inserir(L, novoProduto(1, "produto1"));
  inserir(L, novoProduto(2, "produto2"));
  inserir(L, novoProduto(3, "produto3"));
  inserir(L, novoProduto(4, "produto4"));
  inserir(L, novoProduto(5, "produto5"));
  imprimir(L);
  ...
 };

```

---

### Listas

Note que a lista já armazena seu próprio tamanho:

```
void imprimir(Lista L){
  for(int i=0;i < L.n ; i++){
  ...

```

```

/******************************************************************************
Exemplo :
=> Crie um tipo estruturado para representar uma medição
de temperatura em um sensor, considerando-se que este
registro contém a temperatura observada(numero real)
e o codigo de identificação do sensor(sequência alfanumérica)
******************************************************************************/

#include <iostream>
#define MAX 10

struct Sensor{

char cod[MAX];
float temperatura;

};

using namespace std;

int main()
{
    // essa variavel funcionara como um conteiner
    Sensor s;

    cout << "Informe o codigo do sensor: ";
    cin >> s.cod;

    cout << "Informe a temperatura: ";
    cin >> s.temperatura;

    cout << "Sensor " << s.cod << ": " << s.temperatura << endl;

    return 0;
}

```

---

```
/******************************************************************************
Crie uma estrutura Data, com campos dia, mes e ano, e escreva um
programa que lê as datas de nascimento de duas pessoas e determina
quem é a mais velha.

Para isso, crie uma função que recebe duas datas, d1 e d2 , e retorna 1
se d1 é a data mais antiga, 0 se as duas datas são iguais, e −1 se d2 é a
data mais antiga.
*******************************************************************************/

#include <iostream>
#include <iomanip>

using namespace std;

struct Data{
     int dia;
     int mes;
     int ano;
};

void lerData(Data &d){
	cin >> d.dia >> d.mes >> d.ano;
}

void imprimeData(Data &d){
	cout << setw(3) << setfill('0') << d.dia << "/" << setw(3) << setfill('0') << d.mes  << "/" << d.ano;
}
int compara(Data d1, Data d2){
//comparar o ano
if(d1.ano < d2.ano ){
	return 1;
}else if(d2.ano  < d1.ano){
	return -1;
}else if(d1.mes < d2.mes){
	return 1;
}else if(d2.mes < d1.mes){
	return -1;
}else if (d1.dia < d2.dia){
	return 1;
}else if(d2.dia < d1.dia){
	return -1;
}else{
	return 0;
}
}

int main()
{
    Data d1, d2;

int x1, x2;

lerData(d1);
lerData(d2);
imprimeData(d1);
imprimeData(d2);
//width - > Largura;
//cout << setw(3) << setfill('0') << d1.dia << "/" << setw(3) << setfill('0') << d1.mes  << "/" << d1.ano;

int res = compara(d1, d2);
if(res == 1){
cout << "Data 1 é mais antiga" << endl;
}else if(res == -1){
 cout << "Data 2 é mais antiga" << endl;
}else{
cout << "As datas são iguais: " << endl;
}

    return 0;
}

```

---

```
/******************************************************************************
Escreva um programa para calcular a distância entre dois pontos no plano
catersiano. O seu programa deve ter uma estrutura Ponto, com campos
x e y, e uma função que recebe dois pontos e retorna o quadrado da distância
entre eles.
*******************************************************************************/

#include <iostream>

using namespace std;

struct Ponto{
	int x;
	int y;
};

void lePonto(Ponto &p){
	cout << "Digite os pontos: " << endl;
	cin >> p.x >>p.y;
}

void imprimirPonto(Ponto p){
 cout << "Pontos Digitados: " << endl;
 cout << "(" << p.x << ", " << p.y << ")" <<endl;
}

//uma Função recebe dois pontos e retorna o quadrado da distancia
int calcDistabcia(Ponto p1, Ponto p2){
int distX = p1.x - p2.x;
int distY = p1.y - p2.y;

return distX * distX + distY * distY;
}

int main()
{
    Ponto p1,p2;

    //Lê e imprimir os valores dos pontos;
    lePonto(p1);
    lePonto(p2);
    imprimirPonto(p1);
    imprimirPonto(p2);

		//Calcular a distancia;
    int res = calcDistabcia(p1,p2);

    cout << "A distancia é " << res << endl;

    return 0;
}

```

---

```
/*
Produtos Defina um tipo estruturado denominado Produto que possibilite o
armazenamento das seguintes informações: Nome (string) Codigo (número inteiro)
Preco (número real) Tipo (pode ser (0) Electrodoméstico, (1) Moda ou (2) Outros)
Utilizando o tipo Produto: - Faça uma função para imprimir as informações de um
produto -Faça uma função que retorna o produto mais caro de um vetor de produtos.
-Faça uma função que retorne true se o produto "iPad" está contido em um vetor
de produtos. -Faça uma função que retorne o lucro que a loja teria caso vendesse
todos os electrodomésticos. O seu main deve ler n produtos, imprimir todos os
produtos, imprimir o produto mais caro, dizer se existe iPad nos produtos e
retornar o lucro que a loja teria caso vendesse todos os electrodomésticos.
Entrada 						saida
2								{ código: 2323 , nome: iPad , preço: 999.99 , tipo = Outro }
iPad							{ código: 1212 , nome: Microondas , preço: 499.99 , tipo = Eletrodoméstico }
2323							Mais caro
999.99							{ código: 2323 , nome: iPad , preço: 999.99 , tipo = Outro }
2								Tem iPad
Microondas						Lucro: 499.99
1212
499.99
0
*/
#include <iostream>
#include <cstring>
#define MAX 100
using namespace std;

struct Produto{
    char Nome[MAX];
    int Codigo;
    double Preco;
    int Tipo;
};

void LeinfoNome(Produto &p){
    cin.getline(p.Nome, MAX);
    cout << "insira o codigo: ";
    cin >> p.Codigo;
    cout << "Insira o preço: ";
    cin >> p.Preco;
    cout << "Insira o tipo: ";
    cin >> p.Tipo;
}

void infoProdutos(const Produto p){
    cout << "{ ";
    cout << "código: " << p.Codigo;
    cout << " , ";
    cout << "nome: " << p.Nome;
    cout << " , ";
    cout << "preço: " << p.Preco;
    cout << " , ";
    if(p.Tipo == 0){
        cout << "tipo = Eletrodoméstico";
    }
    else if(p.Tipo == 1){
        cout << "tipo = Moda";
    }
    else if(p.Tipo == 2){
        cout << "tipo = Outro";
    }
    cout << " }" << endl;
}

Produto pMaisCaro(Produto p[], int n){
    Produto maisCaro = p[0];
    for(int i = 0; i < n; i++){
        if(p[i].Preco > maisCaro.Preco){
            maisCaro = p[i];
        }
    }

    return maisCaro;
}

bool TemIpad(Produto p[], int n){
    for(int i = 0; i < n; i++){
        if(strcmp(p[i].Nome, "iPad") == 0){
            return true;
        }
    }

    return false;
}

float Lucro(Produto p[], int n){
    float lucro = 0.0;
    for(int i = 0; i < n; i++){
        if(p[i].Tipo == 0){
            lucro = lucro + p[i].Preco;
        }
    }
    return lucro;
}
int main(){
    int n;

    Produto p[MAX];
    cout << "Informe a quantidade de produtos: ";
    cin >> n;

    for(int i = 0; i < n; i++){
        cin.ignore();
        LeinfoNome(p[i]);
        infoProdutos(p[i]);
    }

    cout << "Mais caro" << endl;

    infoProdutos(pMaisCaro(p,n));

    if(TemIpad(p,n) == true){
        cout << "Tem iPad" << endl;
    }
    else{
        cout << "Não tem iPad" << endl;
    }

    cout << "Lucro: " << Lucro(p,n) << endl;
    return 0;
}

```

# LAB 1

```
/******************************************************************************
(Pacientes) - Uma certa região tem cadastrado seus habitantes para vacinação. Para isto,
alguns dados são necessários, são eles:
- Nome;
- Idade;
- Comorbidade.
Construa um programa C++ que armazene as informações apenas para três pessoas,
e informe qual deles tem prioridade para vacinação. A prioridade deve ser dada para
os pacientes com comorbidades (0-não, 1-sim). A saída deve informar apenas o nome das
pessoas com prioridade para vacinação ou caso não exista comorbidades, informar:
"Sem pacientes com prioridade".
*******************************************************************************/

#include <iostream>
#define MAX 100

using namespace std;

struct Paciente{
    char nome[MAX];
    int idade;
    bool comorbidade = false;
};

void lerDados(Paciente &p){
    cout <<"Digite o nome do paciente: ";
    cin >> p.nome;

    cout << "Digite  sua idade: ";
    cin >> p.idade;

    cout << "Possui comorbidade: ";
    cin >> p.comorbidade;
}

int main()
{
    Paciente p1 , p2 , p3;

    lerDados(p1);
    lerDados(p2);
    lerDados(p3);

    if((p1.comorbidade && p2.comorbidade)){
        cout << p1.nome << " " << p2.nome <<  endl;
    }else if((p1.comorbidade == 1 && p3.comorbidade)){
        cout << p1.nome << " " << p3.nome <<  endl;
    }else if(p2.comorbidade == 1  && p3.comorbidade){
        cout << p2.nome << " " << p3.nome << endl;
    }else if(p1.comorbidade){
        cout << p1.nome <<  endl;
    }else  if(p2.comorbidade){
        cout << p2.nome <<  endl;

    }else  if(p3.comorbidade){
        cout << p3.nome <<  endl;
    }else{
        cout << "Sem pacientes com prioridade" << endl;
    }

    return 0;
}

```

```
/******************************************************************************
(Veículos) - Defina um tipo estruturado que sirva para representar um veículo, considerando os seguintes dados:
- Modelo;
- Marca;
- Ano de Fabricação;
- Preço.
Depois, escreva um programa no qual o usuário deve informar para cadastro,
os dados de dois veículos. Por fim, imprima o modelo e marca do veículo mais
antigo. Caso ambos os veículos tenham sido fabricados no mesmo ano, informe
a frase "Mesmo ano de fabricação".

Gol VW 2000 29999.99 Fiesta Ford 2000 29999

HB20 Hyundai 2015 34615.88 Polo VW 2014 34220.12
*******************************************************************************/

#include <iostream>
#define MAX 100

using namespace std;

struct Veiculo{
    char modelo[MAX];
    char marca[MAX];
    int ano;
   float preco;
};

void lerDados(Veiculo &v){
    cout <<"Modelo: ";
    cin >> v.modelo;

    cout << "Marca: ";
    cin >> v.marca;

    cout << "Ano: ";
    cin >> v.ano;

    cout << "Preço: ";
    cin >> v.preco;
}

int main()
{
    Veiculo v1 , v2;

    lerDados(v1);
    lerDados(v2);

    if(v1.ano < v2.ano){
        cout << v1.modelo << " "  << v1.marca << endl;
    }else if(v2.ano < v1.ano){
        cout << v2.modelo << " " << v2.marca << endl;
    }else {
        cout << "Mesmo ano de fabricação" << endl;
    }
    return 0;
}

```

---

```
#include <iostream>

using namespace std;

const int MAX = 50;

struct Times{
  char time[MAX];
  int pontos;
};

void dados(Times &t){
  cin.getline(t.time, MAX);
  cin >> t.pontos;
}

void Classificacao(const Times t){
	cout << t.time << ", " << t.pontos << " ponto(s)" << endl;
}

Times tMaiorPonto(Times t[], int n){
    Times maiorPontuador = t[0];
    for(int i = 0; i < n; i++){
        if(t[i].pontos > maiorPontuador.pontos){
            maiorPontuador = t[i];
        }
    }

    return maiorPontuador;
}

int main(){
  int n;

  Times t[MAX];

  cin >> n;

  for(int i = 0; i < n; i++){
    cin.ignore();
  	dados(t[i]);
    //Classificacao(t[i]);
  }

  Classificacao(tMaiorPonto(t,n));
  return 0;
}

```

---

```
/*  LAB LIP
 Um sistema de vacinação possui (N<=100) vagas para vacinação durante o dia. Escreva um programa que cadastre em um vetor,
N pessoas que serão vacinadas, isto deve ser feito utilizando structs. No cadastro, serão necessários apenas o campos Nome
e Idade. Depois, imprima na saída o primeiro nome a ser vacinado considerando o de maior idade. Utilize funções para
solução do problema. Exemplo:

Entada : => 3 Fulano 25 Beltrano 75 Cicrano 42                 Saída => Beltrano
            4 Fulano 55 Beltrano 25 Cicrano 99 Jose 33                  Cicrano
*/

#include <iostream>
#define MAX 100

using namespace std;

struct Cadastro{
    char nome[MAX];
    int idade;

};

void lerDados(Cadastro &c){
    cout <<"Digite o nome do paciente: ";
    cin >> c.nome;

    cout << "Digite  sua idade: ";
    cin >> c.idade;
}

int main()
{
    Cadastro c[MAX];
    int n, ida = 0;
    int  aux;
    cout << "Quantidade de Pacientes: ";
    cin >> n;

    for(int i = 0;i < n;i++){
         lerDados(c[i]);
    }

        ida = c[0].idade;

    for(int i = 0;i < n;i++){
        if(c[i].idade > ida){
            aux = i;
            ida = c[i].idade;
         }
         cout << "AUX = " << aux << endl;
      }

    cout << "A pessoa de maoir idade é "<< c[aux].nome << endl;

    return 0;
}

```

# LOP

```
/*
Escreva um programa que lê as coordenadas no plano cartesiano de um ponto
p e em seguida lê um inteiro n e as coordenadas de n pontos. Seu programa deve
dizer qual dos n pontos é o ponto mais próximo de p. O seu programa deve ter
uma estrutura Ponto, com campos x e y, e uma função que recebe dois pontos e
retorna a distância entre eles.
Entrada: 0  0  2  1  1  1  2
saida: Ponto mais perto é (1, 1)
*/

#include <iostream>
#define MAX 10

using namespace std;

struct Ponto{
	int x;
	int y;
};

void lePonto(Ponto &p){
	cout << "Digite os pontos: " << endl;
	cin >> p.x >>p.y;
}

void imprimirPonto(Ponto p){
 cout << "Pontos Digitados: " << endl;
 cout << "(" << p.x << ", " << p.y << ")" <<endl;
}

//uma Função recebe dois pontos e retorna o quadrado da distancia
int calcDistabcia(Ponto p1, Ponto p2){
int distX = p1.x - p2.x;
int distY = p1.y - p2.y;

return distX && distY ;
}

int main()
{
    Ponto q1, p[MAX];

    lePonto(q1);
    imprimirPonto(q1);

    int n ;
    cout << "Quantos vetores? ";

    cin >> n ;
    //Lê e imprimir os valores dos pontos;

    for(int i = 0;i < n;i++){
        lePonto(p[i]);
        imprimirPonto(p[i]);
    }
		//Calcular a distancia;
    int res;
    for(int i = 0;i < n;i++){
        res = calcDistabcia(q1,p[i]);
    }

    cout << "A distancia é " << res << endl;

    return 0;
}

```

### Estrutura Aninhadas: Estrutura como campo de estrutura

Exemplo:

```
struct Ponto{
float x, y;
};

int main(){
Ponto p;
return 0;
};

```

## Estrutura Aninhadas

## Exemplos de Aula:

```
/******************************************************************************
Exemplo:
=> Defina uma estrutura que represente uma pessoa
	=> Nome Completo;
	=> Data de Nascimento;
=>Faça a leitura e impressão de seus dados;
*******************************************************************************/

#include <iostream>
#define MAX_NOME 50

using namespace std;

struct Data{
	int dia, mes, ano;
};

struct Pessoa{
	char nomeCompleto[MAX_NOME];
	Data nascimento;
};

int main()
{
    Pessoa p;

    cout << "Informe o nome completo: ";

    cin.getline(p.nomeCompleto, MAX_NOME);

    cout << "Informe a data de nascimento (dd mm aa): ";

    cin >> p.nascimento.dia >> p.nascimento.mes >> p.nascimento.ano;

    cout << "Dados lidos: " << endl;

    cout << "Nome Completo: " << p.nomeCompleto << endl;

    cout << "Nascimento: " <<  p.nascimento.dia << "/" << p.nascimento.mes << "/" << p.nascimento.ano << endl;

    return 0;
}

```

# **Vetores de tipo estruturado**

Arrays de tipos estruturados;

Em um array  de um tipo de dado primitivo, todos os elementos são
daqueles tem primitivo;

Em um array de um tipo estruturado, cada elemento do vetor contém todos
os campos deste tipo estruturado;

```
/******************************************************************************
Exemplo:

=> Crie um programa no qual são cadastradas n pessoas. Os dados de cada
pessoa são:
 	=>Nome;
	=>Idade;
	=>Salário;
=> Mostre quantas pessoas entre 25 e 30 anos recebem acima de R$2.500,00;
=> Mostre qual a média salarial, considerando todas as pessoas;

*******************************************************************************/

#include <iostream>
#define MAX_NOME 50
#define MAX_N 100
using namespace std;

struct Pessoa{
	char nome[MAX_NOME];
	int idade;
	float salario;
};

int main()
{
    int n, cont =0;
    float somaSalario = 0.0, media;

    Pessoa v[MAX_N];

    cout << "Informe a quantidade: ";
    cin >> n;

    for(int i = 0;i < n;i++){

    	//para não ignorar os valores;
    	cin.ignore();

    	cout << "Informe o nome: ";
    	cin.getline(v[i].nome, MAX_NOME);

    	cout << "Infome a idade: ";
    	cin >> v[i].idade;

    	cout << "Informe o salario: ";
    	cin >> v[i].salario;
    }
    for(int i = 0;i < n;i++){
	if(v[i].idade >=25 && v[i].idade <=30 && v[i].salario > 2500){
		cont++;
	}
	somaSalario = somaSalario + v[i].salario;
}
    media = somaSalario/n;

    cout << "Relatorio: "<< endl;
    cout << "Acima de R$ 2500 (25 - 30): " << cont << endl;
    cout << "Media Salarial: " << media << endl;

    return 0;
}

```

Funções recursivas

Conceito:
=> Função que se refere a ela mesma
=> Lógica da função possui chamadas diretas ou indiretas á propria função

Exemplo:

```
int funcao(int x){
			if(x == 0){
					return 1;
			}else{
					cout << x << endl;
					return funcao(x-1);
			}
}

```

A propria função se chama dentro do codigo;

exemplo de fatorial recursivo:

main, n = 4: fatRec(4)
fatRec, n = 4 : 4 * (fatRec(3) -> 6) = 24
fatRec, n = 3 : 3 * (fatRec(2) -> 2) = 6;
fatRec, n = 2 : 2 * (fatRec(1) -> 1) = 2;
fatRec, n = 1 : 1 * (fatRec(0) -> 1) = 1;
fatRec, n = 0 : 1;

# Aulas YouTube

Função Recursiva

=> Uma função que faz uma chamada para si mesma diretamente
ou indiretamente;
=> Abordagem alternativa;

Função recursiva: elementos
=>caso basico;
=>Recursão;

Exemplo:
0! = 1
1! = 1
2! = 1 * 2
3! = 1 * 2 *3
4! = 1 * 2 * 3 * 4

=> N!;
=>IMPLEMENTAR EM C++

## codigo das aulas

```
#include <iostream>

using namespace std;

// n! = n * (n-1);

int fat(int n);

int main()
{
    cout << fat(4) << endl;
    //fat(4) = 4 * fat(3) = 4* 3 * fat(2) = 4 * 3* 2 * 1 = > assim que a função foi chamada;

    return 0;
}
int fat(int n){
    if(n == 0 || n ==1){
        return 1;
    }else {
        return n * fat(n-1);
    }

}

```

```

#include <iostream>
#define MAX 5
using namespace std;

void imprimir(int v[MAX], int n);

int main()
{
    int v[MAX]= {1, 2, 3, 4, 5};

    int n = 5;

    imprimir(v, n);

    return 0;
}

void imprimir(int v[MAX], int n){
    if(n == 1){
        cout << v[n-1] << " ";
    }else {
        cout << v[n-1] << " "; // imprimindo do ultimo para o primeiro
        imprimir(v, n-1);
        cout << v[n-1] << " "; // imprimindo os elementos na ordem;
    }
}

```

```
#include <iostream>
#define MAX 5
using namespace std;

void imprimir(int v[MAX], int n);

int somar(int v[MAX], int n);

int main()
{
    int v[MAX]= {1, 2, 3, 4, 5};

    int n = 5;

    imprimir(v, n);

    cout << "Soma = " << somar(v, n) << endl;
    return 0;
}

void imprimir(int v[MAX], int n){
    if(n == 1){
        cout << v[n-1] << " ";
    }else {
        cout << v[n-1] << " "; // imprimindo do ultimo para o primeiro
        imprimir(v, n-1);
        cout << v[n-1] << " "; // imprimindo os elementos na ordem;
    }
}

int somar(int v[MAX], int n){
    if(n == 1){
        return v[n-1];
    }else{
        return v[n-1] + somar(v, n-1);
    }

}

```

# Exemplo aula sincrona

```
/*Multiplicação Recursiva e divisão recursiva;
*/

#include <iostream>

using namespace std;

int mulR(int x , int y){
    if(y == 0){
        return 0;
    }else {
           return x + mulR(x, y-1);
    }
}
int divRec(int x, int y){
	if(x < y){
		return 0;
	}else{
		return 1+ divRec(x - y, y);
	}
}

int main()
{   int x , y;
    cout << "Digite os Valores de entrada: ";
    cin >> x >> y;

    cout << "Divisão Recursiva: " << divRec(x, y) << endl;
    cout << endl;
    cout << "Multiplicação Recursiva: " << mulR(x, y) << endl;
    return 0;
}

```

# Plataforma LOP

```
/*
Potencia Defina recursivamente a função potência. Assuma que os parâmetros x e y são inteiros positivos.
ex:
Entrada:                        Saida:
8  3                                pow( 8 , 3 ) = 512
8  2                                pow( 2 , 8 ) = 256

*/

#include <iostream>

using namespace std;

int potRec(int x, int y){
    if(y == 0){
        return 1;
    }else{
        return x * potRec(x , y -1 );
    }
}

int main()
{
    int x, y;

    cout << "Digite o X  elevado Y : ";
    cin >> x >> y;

    cout << "pow( " << x << " , " <<y << " ) = "  << potRec(x, y) << endl;
    return 0;
}

```

```
/*Multiplicação Recursiva e divisão recursiva;
*/

#include <iostream>

using namespace std;

int mulR(int x , int y){
    if(y == 0){
        return 0;
    }else {
           return x + mulR(x, y-1);
    }
}

}

int main()
{   int x , y;
    cout << "Digite os Valores de entrada: ";
    cin >> x >> y;

    cout << "Multiplicação Recursiva: " << mulR(x, y) << endl;
    return 0;
}

```

```
/*
Considere as seguintes operações em um inteiro positivo n: - se n for par, divida-o por 2 - se n for ímpar,
multiplique-o por 3 e some 1A conjectura de Collatz diz que, para qualquer número n>0, quando as regras acima
são aplicadas, eventualmente sempre chegaremos a 1. Faça uma função recursiva que, dado um número n>0, retorne
o número de passos para chegar a 1.

f(n) = { n/2, se n é par
       { 3n + 1, se é impar

       8              5
    8,4,2,1         5, 15+1, 8 , 4 ,2 ,1
*/

#include <iostream>

using namespace std;

int conj(int n){

    cout << "Valor de n = " << n << endl;

    if(n == 1){
        return 0;
    }else{
        if(n % 2 == 0){
            return 1 + conj(n/2);
        }else{
             return 1 + conj(n+n+n+1);
        }
    }

}

int main()
{
    int n, res;
    cout << "Digite um numero: ";
    cin >> n;

    res = conj(n);
    cout << "Números de passos: " << res << endl;
    return 0;
}

```

```
/*
Considere o método a seguir para calcular o Máximo Divisor Comum de dois números x e y: - Se y=0,
MDC(x,y) = x. - Caso contrário, calcule o MDC de y e o resto da divisão x % y. Implemente uma função
para calcular o MDC como descrito acima.
10
2	          MDC(10 , 2) = 2
*/

#include <iostream>
#define MAX 30

using namespace std;

void leDivisor(int &x, int &y){
    cout << "Digite os valores para x e y: ";
    cin >> x >> y;
}
int  divRec(int x, int y){
    int mdc;
    if(y == 0){
        return x;
    }else if(x == 0){
        return y;
    }else{
        if ( x < y ) {
            mdc = x ;
        }
        else{
            mdc = y ;
        }
        while ( x % mdc != 0 || y % mdc != 0) {
            mdc --;
       }
            return mdc ;
        }
    }

int main(){
    int x, y, res;

    leDivisor(x, y);
    res = divRec(x, y);

    cout << "MDC(" << x <<", " << y << ") = " << res << endl;
    return 0;
}

```

#Algoritmo e Ordenação:

=> Reorganizar os elementos de um conjunto de forma ordenada
(crescente ou decrescente) de acordo com algum critério:

=> {3, 2, 5} --> {2, 3, 5}
=> {0.1, 0.4, 0.0} --> {0.0, 0.1, 0.4}
=> {"Maria", "João", "Alice"} --> {"Alice","João","Maria"}

## Metodos:

Exemplos: Bubble sort, insertion sort, seletion sort, Merge sort,
Heap sort, Quick sort

## Bubble sort(Metodo Bolha)

=> Mova o maior elemento para o ultimo índice do vetor;
=> Mova o segundo maior elemento do vetor para o penúltimo índice do vetor;
=>... E assim sucessivamente até que o vetor esteja ordenado

## Codigos de aula

```
/*
                            Metodo Bolha
*/

#include <iostream>
#define MAX 10

using namespace std;

int main(){
    int v[MAX] = {3, 1, 9,3, 4, 5, 6, 8, 0,2};

    int n = 10;

    //A variavel ultimo registrar o ultimo indice do vetor;
    int ultimo = n-1, aux; // a variavel auxiliar sempre será do mesmo tipo do vetor;

    bool troca; // server para organizar e dizer se o vetor está na ordem;

    do{
        troca = false;
        for(int j = 0;j < ultimo;j++){
                //testando se há elementos fora de orde,
            if(v[j] > v[j+1]){
                troca = true;
                aux = v[j];
                v[j] = v[j +1];
                v[j + 1]  = aux;
            }
        }
        //atualiza o ultimo elemento do vetor;
        ultimo--;
    }while(troca == true);

        // n -> n * n -> para retornar o tamanho do vetor;
        //sort -> função em c++ para ordenado os valores, n*log(n)

    cout << "Vetor Ordenado: ";
    for(int i = 0;i < n;i++ ){
        cout << v[i] << " ";
    }

    return 0;
}

```

## Ordenando um vetor de estruturas com funções:

```
/*
Lista de Alunos

=> Uma lista de alunos foi armazenada em um vetor
de estruturas: Nome Completo, Notas e Idade;

=> Mostre a média das notas dos k melhores alunos;
=> Mostre a lista de alunos ordenada de acordo com o nome;
*/

#include <iostream>
#include <cstring>
#define MAX 10
#define MAX_NOME 30

using namespace std;

struct Aluno{
    char nomeCompleto[MAX_NOME];
    int idade;
    float nota;
};

void ordenarPelaNota(Aluno v[MAX], int n);
void ordenarPeloNome(Aluno v[MAX], int n);
void trocar(Aluno &a, Aluno&b);

int main(){
    int n = 10;
    int k = 3;
    float soma = 0.0, media = 0.0;

    Aluno v[MAX] = {{"Luan",18,7.5},
                    {"Allan",19,7.0},
                    {"Sonia",20,6.5},
                    {"Beth",17,8.5},
                    {"Cleber",16,9.5},
                    {"Jose",22,10.0},
                    {"Maria",24,5.6},
                    {"Joao",17,3.5},
                    {"Luciana",16,4.89},
                    {"Jefferson",15,5.8} };

    ordenarPelaNota(v, n);
    for(int i = 0;i < k;i++){
        soma = soma + v[i].nota;
    }
    media = soma/k;

    cout << "Media dos  " << k << " melhores alunos; " << media << endl;

    //Rearranja o vetor na ordem alfabetica
    ordenarPeloNome(v , n);

    cout << "Lista Ordenada Alfabeticamente: " << endl;

    for(int i = 0;i < n;i++){
        cout << v[i].nomeCompleto << ", " << v[i].idade << ", " << v[i].nota << endl;
    }

    return 0;
}

void ordenarPelaNota(Aluno v[MAX], int n){
    int ultimo = n - 1;
    bool troca;

    do{
        troca = false;

        for(int j = 0 ;j < ultimo;j++){
            if(v[j].nota < v[j+1].nota){
                troca = true;
                trocar(v[j], v[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}

void ordenarPeloNome(Aluno v[MAX], int n){
    int ultimo = n -1;
    bool troca;

    do{
        troca = false;

        for(int j = 0;j < ultimo;j++){
            //para comparar duas cadeias de caracteres strcmp
            // valor positivo  v[j] vem primeiro         negativo  v[j + 1] vem primeiro          iguais = 0
            if(strcmp(v[j].nomeCompleto, v[j+1].nomeCompleto) > 0){
                troca = true;
                //a função troca de posição todos os valores das posições dentro do vetor;
                trocar(v[j], v[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}

void trocar(Aluno &a, Aluno&b){
    Aluno aux;
    aux = a;
    a = b;
    b = aux;
}

```

# Aula Sincrona

```
/*
O seu programa deve ler um número n <= 30 e em seguida
ler as datas de nascimento de n pessoas.

O seu programa deve ordenar as datas de nascimento da
mais antiga para a mais nova e imprimi-las.

Crie uma função auxiliar que recebe duas datas, d1 e d2 , e retorna 1
se d1 é a data mais antiga, 0 se as duas datas são iguais, e −1 se d2 é
a data mais antiga.
*/

#include <iostream>
#include <cstring>
#define MAX 30
#define MAX_NOME 30

using namespace std;

struct Data{
    int dia, mes, ano;
};

void leData(Data datas[], int n){
    cout << "Insira a data: ";
    for(int i = 0;i < n;i++){
        cin >> datas[i].dia >> datas[i].mes >> datas[i].ano;
    }
}

void imprimeData(Data datas[], int n){
        cout << "A data e : ";
    for(int i = 0;i < n;i++){
        cout << datas[i].dia << " "<< datas[i].mes << " "<< datas[i].ano << endl;
    }
}
int comparaData(Data d1, Data d2){
    if(d1.ano != d2.ano){
        if(d1.ano < d2.ano){
            return 1;
        }else{
            return-1;
        }
    }else if(d1.mes != d2.mes){
        if(d1.mes < d2.mes){
            return 1;
        }else{
            return-1;
        }
    }else if(d1.dia =! d2.dia){
        if(d1.dia < d2.dia){
            return 1;
        }else{
            return-1;
        }
    }else {
        return 0;
    }

}

void trocarData(Data &d1, Data &d2){
    Data aux;
    aux = d1;
    d1 = d2;
    d2 = aux;
}

void ordenaDatas(Data datas[], int n){
    int ultimo = n - 1, aux = 0;
    bool trocou = false;
    do{
        trocou = false;
        for(int j = 0;j < ultimo;j++){
            if(comparaData(datas[j], datas[j+1]) == -1){
                trocarData(datas[j], datas[j+1]);
                trocou = true;
            }
        }
        ultimo--;
    }while(trocou == true);

}

int main(){
    Data datas[MAX];
    int n;

    cout << "Insira a quantidade de datas: ";
    cin >> n;

    leData(datas, n);
    imprimeData(datas, n);

    cout << comparaData(datas[0], datas[1]) << endl;
    cout << comparaData(datas[1], datas[2]) << endl;
    ordenaDatas(datas, n);
    imprimeData(datas, n);
    return 0;
}

```

Resposta Multiprova:

v (0 ,1 )(0,2) (1, 0) (1, 1) (1, 2)

vord (0,2) (0,1) (1, 2) (1, 1) (1, 0)

Alternativas: (F)(V)(F)

# Plataforma LOP

```
/*
O seu programa deve ler um número n <= 30 e em seguida
ler as datas de nascimento de n pessoas.

O seu programa deve ordenar as datas de nascimento da
mais antiga para a mais nova e imprimi-las.

Crie uma função auxiliar que recebe duas datas, d1 e d2 , e retorna 1
se d1 é a data mais antiga, 0 se as duas datas são iguais, e −1 se d2 é
a data mais antiga.
*/

#include <iostream>
#include <cstring>
#define MAX 30
#define MAX_NOME 30

using namespace std;

struct Data{
    int dia, mes, ano;
};

void leData(Data datas[], int n){
    cout << "Insira a data: ";
    for(int i = 0;i < n;i++){
        cin >> datas[i].dia >> datas[i].mes >> datas[i].ano;
    }
}

void imprimeData(Data datas[], int n){
        cout << "A data e : ";
    for(int i = 0;i < n;i++){
        cout << datas[i].dia << " "<< datas[i].mes << " "<< datas[i].ano << endl;
    }
}
int comparaData(Data d1, Data d2){
    if(d1.ano != d2.ano){
        if(d1.ano < d2.ano){
            return 1;
        }else{
            return -1;
        }
    }else if(d1.mes != d2.mes){
        if(d1.mes < d2.mes){
            return 1;
        }else{
            return -1;
        }
    }else if(d1.dia != d2.dia){
        if(d1.dia < d2.dia){
            return 1;
        }else{
            return -1;
        }
    }else{
        return 0;
    }

}

void trocarData(Data &d1, Data &d2){
    Data aux;
    aux = d1;
    d1 = d2;
    d2 = aux;
}

void ordenaDatas(Data datas[], int n){
    int ultimo = n - 1, aux = 0;
    bool trocou;
    do{
        trocou = false;
        for(int i = 0;i < ultimo;i++){
            if(comparaData(datas[i], datas[i+1]) == -1){
                trocarData(datas[i], datas[i+1]);
                trocou = true;
            }
        }
        ultimo--;
    }while(trocou == true);
}

int main(){
    Data datas[MAX];
    int n;

    cout << "Insira a quantidade de datas: ";
    cin >> n;

    leData(datas, n);
    imprimeData(datas, n);

    cout << comparaData(datas[0], datas[1]) << endl;
    cout << comparaData(datas[1], datas[2]) << endl;

    cout << "Datas Ordenadas: " << endl;
    ordenaDatas(datas, n);
    imprimeData(datas, n);
    return 0;
}

```

```
/*
Ordenando um vetor: Escreva uma função que recebe um array de inteiros v, o seu número de elementos n,
e ordena os elementos de v em ordem decrescente. Faça um programa que lê a dimensão do vetor, os elementos
dele e depois imprime o vetor ordenado.
*/

#include <iostream>
#define MAX 30

using namespace std;

void leVetor(int v[], int n){
    cout << "Insira os dados do vetor: ";
    for(int i = 0;i < n;i++){
        cin >> v[i];
    }
}

void imprimeVetor(int v[], int n){
    cout << "O vetor e [ ";
    for(int i = 0;i < n;i++){
        cout << v[i] << "";
        if(i < n -1){
            cout << ", " << "";
        }
    }
    cout << "]" << endl;
}

void ordenaVetor(int v[], int n){
    int ultimo = n - 1, aux = 0;
    bool trocou;
    do{
        trocou = false;
        for(int i = 0;i < ultimo;i++){
            if(v[i] < v[i+1]){
                trocou = true;
                aux = v[i];
                v[i] = v[i +1];
                v[i + 1]  = aux;
            }
        }
        ultimo--;
    }while(trocou == true);
}

int main(){
    int v[MAX];
    int n;

    cout << "Quantos n valores: ";
    cin >> n;

    leVetor(v, n);
    imprimeVetor(v, n);

    ordenaVetor(v, n);

    imprimeVetor(v, n);

    return 0;
}

```

```
/*
Ordenando uma stringCrie uma função que recebe um cadeia de caracteres s, formada apenas por letras minúsculas, e ordena os caracteres de
s de acordo com o seguinte critério:a) As vogais devem aparecer antes das consoantes.b) Após aplicar o primeiro critério, as vogais e as
consoantes devem ser ordenadas em ordem alfabética.
pneumartrorradiografia
aaaaeiiooudfgmnprrrrrt

*/
#include<iostream>
#include<cstring>
#define MAX 50
using namespace std;

void ordenar(char v[], int n);
void trocar(char &a, char &b);

int main(){
    char v[MAX];
    cin.getline(v, MAX);
    int n = strlen(v);
    for(int i=0; i<n; i++){
        cout << v[i];
    }
    cout << endl;
    ordenar(v, n);
    for(int i=0; i<n; i++){
        if(v[i] == 'a' || v[i] == 'e' || v[i] == 'i' || v[i] == 'o' || v[i] == 'u'){
            cout << v[i];
        }
    }
    for(int i=0; i<n; i++){
        if(v[i] != 'a' && v[i] != 'e' && v[i] != 'i' && v[i] != 'o' && v[i] != 'u'){
            cout << v[i];
        }
    }

    return 0;
}

void ordenar(char v[], int n){
    int ultimo = n-1;
    bool troca;
    do{
        troca = false;
        for(int i=0; i<ultimo; i++){
            if(v[i] > v[i+1]){
                troca = true;
                trocar(v[i], v[i+1]);
            }
        }
        ultimo--;
    }
    while(troca == true);
}

void trocar(char &a, char &b){
    char aux;
    aux = a;
    a = b;
    b = aux;
}

```

```
/*
Ordenar Par-ímpar: Escreva uma função que recebe um array de inteiros v e o seu número de elementos n.
Essa função deve ordenar v da seguinte maneira: os elementos nos índices pares devem ser ordenados em
ordem não-decrescente, e os elementos nos índices ímpares devem ser ordenados em ordem não crescente.
10
0
12
19
17
17
6
8
7
4
8           [ 0 , 12 , 19 , 17 , 17 , 6 , 8 , 7 , 4 , 8 ]
            [ 0 , 17 , 4 , 12 , 8 , 8 , 17 , 7 , 19 , 6 ]
*/

#include <iostream>
#define MAX 30

using namespace std;

void leVetor(int v[], int n){
    for(int i = 0;i < n;i++){
        cin >> v[i];
    }
}
void troca (int &x, int &y)
{
    int aux = x;
    x = y;
    y = aux;
}

void imprimeVetor(int v[MAX], int n){
    cout << "[ ";
    for(int i = 0;i < n ;i++){
        cout << v[i] <<"";
         if(i < n -1){
            cout << ", " << "";
        }
    }cout << " ]" << endl;
}
void ordenaCrescente (int v[], int n){
    int ultimo = n-1;
    bool trocou = true;

    do {

        trocou = false;

        for (int i = 0; i < n; i++){
            if(v[i] > v[i+1]){
                troca(v[i], v[i+1]);
                trocou = true;
            }
        }
        ultimo--;
    }while (trocou == true);

}

void ordenaDecrescente(int v[MAX], int n){
    int ultimo = n-1;
    bool trocou = true;

    do {
        trocou = false;
        for (int i = 0; i < ultimo; i++){
            if(v[i] < v[i+1])
            {
                troca(v[i], v[i+1]);
                trocou = true;
            }
        }
        ultimo--;
    }while (trocou == true);
}

void ordenar(int v[], int n){
    int vPares[MAX];
    int vImpares[MAX];

    int nPares = 0, nImpares = 0;
    for (int i = 0; i < n; i++){
        if(i % 2 == 0){
            vPares[nPares] = v[i];
            nPares++;
        }else{
            vImpares[nImpares] = v[i];
            nImpares++;
        }
    }

    //Vetor Ordenado apartir das chamadas dos seguintes vetores;
    ordenaCrescente (vPares,nPares);
    ordenaDecrescente (vImpares, nImpares);

    int iPares = 0, iImpares = 0;
    for(int i = 0; i < n; i++){
        if (i % 2 == 0){
            v[i] = vPares[iPares];
            iPares++;
        }else{
            v[i] = vImpares[iImpares];
            iImpares++;
        }
    }

}

int main(){
    int n;
    int v[MAX];
    cin >> n;

    leVetor(v, n);
    imprimeVetor(v, n);

    ordenar(v, n);
    imprimeVetor(v, n);

    return 0;
}

```

# LAB

```
/*
(Ordenação-Notas) Considerando um vetor (N<=50) composto pelas notas dos alunos de uma certa disciplina.
Escreva um programa que realize sua ordenação na ordem crescente. Depois, exiba o índice de todas as notas
que estão igual ou acima da média 5.0. Implemente o método da bolha (Bubble Sort) para ordenação.
Obs: Primeiro deve ser lido o tamanho do vetor, depois todos os seus valores.
*/

#include <iostream>
#define MAX 50

using namespace std;

struct Aluno{
    float nota;
};

void leNota(Aluno notas[], int n){
    cout << "Insira as notas: ";
    for(int i = 0;i < n;i++){
        cin >> notas[i].nota;
    }
}

void imprimeNota(Aluno notas[], int n){
        cout << "A nota e : ";
    for(int i = 0;i < n;i++){
        if(notas[i].nota >= 5.0){
            cout << i << " ";
        }
    }
}

void trocar(Aluno &a, Aluno &b){
    Aluno aux;
    aux = a;
    a = b;
    b = aux;
}

void ordenarPelaNota(Aluno notas[MAX], int n){
    int ultimo = n - 1;
    bool troca;

    do{
        troca = false;

        for(int j = 0 ;j < ultimo;j++){
            if(notas[j].nota > notas[j+1].nota){
                troca = true;
                trocar(notas[j], notas[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}

int main(){
    Aluno notas[MAX];
    float soma = 0.0, media = 0.0;
    int n, k =3;

    cout << "Insira a quantidade de notas: ";
    cin >> n;

    leNota(notas,n);
    imprimeNota(notas, n);
    ordenarPelaNota(notas, n);
    cout << "Ordenadas as notas: ";
    cout << endl;
    imprimeNota(notas, n);

    return 0;
}

```

```
/*
Ordenando NotasVocê é o professor de uma turma de LiP e gostaria de saber a média das k maiores notas da turma.
Escreva uma função que recebe um array com as notas dos alunos da turma, o número de alunos e o valor de k, e retorna
a média das k maiores notas da turma. Seu programa deve ler o valor de k, n e depois as n notas. Utilize o tipo double
e imprima seus resultados com 2 casas decimais.

[ 5.33 , 7.35 , 6.13 , 5.48 , 5.25 , 8.89 , 6.37 , 7.27 , 5.83 , 5.98 ]
Média = 7.84
*/

#include <iostream>
#include <iomanip>
#define MAX 100

using namespace std;

struct Aluno{
    double notas;
};

void leNota(Aluno notas[], int n){
    cout << "Insira as Notas dos Alunos: ";
    for(int i = 0;i < n;i++){
        cin >> notas[i].notas;
    }
}

void imprimeNota(Aluno notas[MAX], int n){
    cout << "O vetor e [ ";
    for(int i = 0;i < n;i++){
        cout << fixed <<  setprecision(2) << notas[i].notas << "";
        if(i < n -1){
            cout << ", " << "";
        }
    }
    cout << "]" << endl;
}

void trocar(Aluno &a, Aluno &b){
    Aluno aux;
    aux = a;
    a = b;
    b = aux;
}

void ordenaPelaNota(Aluno notas[], int n){
    int ultimo = n - 1;
    bool trocou = false;
    do{
        trocou = false;
        for(int i = 0;i < ultimo;i++){
            if(notas[i].notas < notas[i+1].notas){
                trocou = true;
                trocar(notas[i], notas[i+1]);
            }
        }
        ultimo--;
    }while(trocou == true);
}

int main(){
    Aluno notas[MAX];
    int k, n;
    double media = 0.0, soma = 0.0;

    cout << "Insira as k comparações e n notas: ";
    cin >> k >> n;

    leNota(notas, n);
    imprimeNota(notas, n);
    ordenaPelaNota(notas, n);
    cout << "Depois de  Ordenar: ";
    imprimeNota(notas, n);

    for(int i = 0;i < k;i++){
            soma = soma + notas[i].notas;
    }

    media = soma/k;

    cout <<  setprecision(2) << "A Média é: " << media << endl;

    return 0;
}

```

# MULTIPROVA

```

//Ordenar nomes
/*
3
Jefferson Santos
Jonathas Albuquerque
Barbara Siqueira

Barbara Siqueira
Jefferson Santos
Jonathas Albuquerque

*/

#include <iostream>
#include <cstring>
#define MAX 100
using namespace std;

void lerNomes(char m[][MAX], int n){
    char tmp[MAX];
    cin.getline(tmp, MAX);

    for(int i=0; i<n;i++ ){
        cin.getline(m[i], MAX);
    }
 }

 void imprimeNomes(char v[][MAX], int n){

 	for(int i=0; i<n; i++){
 		cout << v[i] << endl;
	 }
	 cout << endl;
 }

void troca(char s1[], char s2[]){
	char aux[MAX];
	strcpy(aux, s1);
	strcpy(s1, s2);
	strcpy(s2, aux);
}

void ordenar(char nomes[][MAX], int n){
	int ultimo = n-1;
	bool trocou = true;
	do{
		trocou= false;
		for(int i=0; i<ultimo; i++){
			if(strcmp(nomes[i], nomes[i+1])>0){
				troca(nomes[i], nomes[i+1]);
				trocou = true;
			}
		}
	}while(trocou == true);
}

int main()
{
    int n;
    char nomes[MAX][MAX];

    cin >> n;

    lerNomes(nomes, n);
    imprimeNomes(nomes, n);

    ordenar(nomes, n);
    imprimeNomes(nomes, n);

    return 0;
}

```

```
/******************************************************************************
Faça uma função para ordenar uma lista de itens. Cada item deve conter as seguintes informações (struct):
Nome do atleta (apenas primeiro nome, sem espaços);
Tempo na prova (em segundos).
Os registros (structs) devem ser ordenados de forma a ter o tempo na prova crescente. Exemplo:
*******************************************************************************/

#include <iostream>
#include <iomanip>
#define MAX 30
using namespace std;

struct Atleta{
    char nome[MAX];
    double tempo;
};

void leAtleta(Atleta a1[], int n){
    cout << "Insira os atletas: ";
    for(int i = 0;i < n;i++){
        cin >> a1[i].nome >> a1[i].tempo;
    }
}
void imprimeAtleta(Atleta a1[MAX], int n){
    for(int i = 0;i < n;i++){
        cout << i+1 << "o" << fixed <<  setprecision(2)<< " colocado - " << a1[i].nome  << " - "<< a1[i].tempo << "s" << endl;
    }
    cout << endl;
}

void troca(Atleta &b, Atleta &c){
    Atleta aux = b;
    b = c;
    c = aux;
}
void ordenaPeloTempo(Atleta a1[], int n){
    int ultimo = n - 1;
    bool trocou = false;
    do{
        trocou = false;
        for(int i = 0;i < ultimo;i++){
            if(a1[i].tempo > a1[i+1].tempo){
                trocou = true;
                troca(a1[i], a1[i+1]);
            }
        }
        ultimo--;
    }while(trocou == true);
}

int main()
{
    Atleta a1[MAX];

    int n;
    cout << "Insira os n atletas: ";
    cin >> n;

    leAtleta(a1, n);
    imprimeAtleta(a1, n);
    ordenaPeloTempo(a1, n);
    imprimeAtleta(a1, n);

    return 0;
}

```

```
/*
(Ordenação-crescente_decrescente) Escreva um programa para ordenar uma série de valores inteiros recebidos na entrada (N < 15).
Seu programa além de ordenar, deve receber a informação se será em ordem crescente "c" ou decrescente "d". Utilize o método de ordenação
que julgar adequado e imprima na saída o resultado desta ordenação. Utilize funções para solução do problema, a main() deve realizar apenas
a leitura dos dados e a chamada das funções. Obs: A entrada de dados deve acontecer até que seja recebido o dígito 0.
Veja o exemplo abaixo:
*/

#include <iostream>
#define MAX 20

using namespace std;

void imprimeVetor(int numero[MAX], int n){
    for(int i = 0;i < n;i++){
        cout << numero[i] << " ";
    }
}

void trocar(int &a, int &b){
    int aux;
    aux = a;
    a = b;
    b = aux;
}

void ordenaCrescente(int numero[MAX], int &n){
    int ultimo = n - 1;
    bool troca;

    do{
        troca = false;

        for(int j = 0 ;j < ultimo;j++){
            if(numero[j] > numero[j+1]){
                troca = true;
                trocar(numero[j], numero[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}
void ordenaDecrescente(int numero[MAX], int &n){
    int ultimo = n - 1;
    bool troca;

    do{
        troca = false;

        for(int j = 0 ;j < ultimo;j++){
            if(numero[j] < numero[j+1]){
                troca = true;
                trocar(numero[j], numero[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}

int main(){

    char nome;
    int numero[MAX];

    int i , n;

    cin >> nome;

    while(numero[i] != 0){
        cin >> numero[i];
	    i++;
    }
    n = i;

    if(nome == 'c'){
        ordenaCrescente(numero, n);
    }else{
        ordenaDecrescente(numero, n);
    }

    imprimeVetor(numero, n);

    return 0;
}

```

# Correção

```
#include <iostream>
#define N 15

using namespace std;

int leitura(int v[]){
	int i = 0;
	while(true){
		cin >> v[i];
		if(v[i] == 0){
			break;
		}
		i++;
	}
	return i++;
}

void impressao(int v[], int tam){
	for(int i =0;i < tam;i++){
		for(int i =0;i < tam;i++){
			cout << v[i] << " ";
		}
		cout << endl;
	}
}

void troca(int &a, int &b){
	int aux = 0;
	a = b;
	b = aux;
}

void ordenacao(char c, int v[], int tam){
	for(int i = 0;i < tam - 1;i++){
		for(int j = 0;j < tam - 1 - i;j++){
			if(c == 'c'){
				if(v[j] > v[j+1]){
					troca(v[j], v[j+1]);
				}
			if(c == 'd'){
				if(v[j] < v[j+1]){
					troca(v[j], v[j+1]);
				}

			}
			}
		}
	}
}
int main(){

    int v[N];
    char c;

    cin >> c;

    int tam = leitura(v);
    ordenacao(c, v, tam);
    impressao(v, tam);

    return 0;
}

```

Questão das vogais

```
#include <iostream>
#include <cstring>
#define N 15

using namespace std;

int leitura(char p[]){
        cin.getline(p, N);
}

void impressao(char p[]){
    int n = strlen(p);
    for(int i = 0;i < n;i++){
        cout << p[i] << " ";
    }
    cout << endl;
}

void ordenacao(char p[]){
int n = strlen(p);
for(int i = 0;i < n - 1;i++){
	for(int j = 0;j < n - 1 - i;j++){
		if(p[j] > p[j+1]){
			char aux = p[j];
			p[j] = p[j +1];
			p[j + 1] = aux;
		}
	}
}
}

int main(){

    char p[N];

    leitura(p);
    ordenacao(p);
    impressao(p);

    return 0;
}

```

```
#include <iostream>
#define MAX 100
using namespace std;

struct Musica{
  char cantor[MAX];
  char titulo[MAX];
  char genero[MAX];
  int quant;
};

void leDados(Musica &m){
  	cin.getline(m.cantor,MAX);
  	cin.getline(m.titulo,MAX);
  	cin.getline(m.genero,MAX);
  	cin >> m.quant;
}
void imprimeDados(Musica m){
  	cout << m.cantor << " - " << m.titulo << " (" << m.genero << ") " << endl;
    cout << "tocada " << m.quant << " vezes" << endl;
}

void imprimeMaisTocados(Musica m){
  	cout  << "Genero mais frequente: " << m.genero <<  endl;

}

void trocar(int &a, int &b){
  int aux;
  aux = a;
  a = b;
  b = aux;
}

void ord(Musica m[MAX], int n){
  int ultimo = n-1;
  bool troca;
  do{
    troca = false;
      for(int i = 0; i < ultimo; i++){
      	if(m[i].quant < m[i+1].quant){
        	troca = true;
          trocar(m[i].quant, m[i+1].quant);
        }
      }
    ultimo--;
  }while(troca == true);
}

int main(){
  Musica m[MAX];

  int n;

  cin >> n;

      for(int i = 0; i < n; i++){
        cin.ignore();
        leDados(m[i]);
				imprimeDados(m[i]);
      }

      ord(m,n);
      for(int i = 0; i < 1; i++){
           imprimeDados(m[0]);
      }
	return 0;
}

/*
Mais tocadas da playlist

Defina um tipo estruturado para representar uma música. Este tipo deve possuir três strings, contendo o artista, título e gênero da música. Além disso,
o tipo estruturado deve conter um campo inteiro para armazenar quantas vezes a música a foi tocada. Em seguida, implemente uma função ord que receba
como parâmetro de entrada um vetor de músicas e o seu tamanho. Este vetor contém uma playlist de músicas, que a função deve ordenar pelas músicas mais tocadas.

A função main do seu programa (ou uma função auxiliar) deve ler uma playlist: primeiro ela deve ler um número N de músicas e em seguida, deve ler  o artista,
título, gênero e quantidade de vezes que uma música foi tocada para cada música da playlist, nesta ordem. Então, o programa deve exibir o vetor conforme ordenado
pela função ord. Por fim, o seu programa deve exibir uma mensagem informando o gênero musical que possui a maior quantidade de músicas na playlist. Isto pode ser
feito na função main ou em uma função auxiliar. Caso mais de um gênero possua a maior quantidade de músicas na playlist, imprima o primeiro que ocorre no vetor
original.

Um exemplo de saída para um vetor com 3 músicas é mostrado a seguir. Utilize a mesma formatação.

Entrada	Saída obtida	Saída esperada
6
"katy perry"
"california gurls"
"pop"
25
"rihanna"
"rude boy"
"pop"
18
"katy perry"
"teenage dream"
"pop"
15
"david guetta"
"sexy bitch"
"eletronica"
10
"lady gaga"
"bad romance"
"pop"
26
"justin bieber"
"baby"
"pop"
16	katy perry - california gurls (pop)
tocada 25 vezes
rihanna - rude boy (pop)
tocada 18 vezes
katy perry - teenage dream (pop)
tocada 15 vezes
david guetta - sexy bitch (eletronica)
tocada 10 vezes
lady gaga - bad romance (pop)
tocada 26 vezes
justin bieber - baby (pop)
tocada 16 vezes
katy perry - california gurls (pop)
tocada 26 vezes	1
lady gaga - bad romance (pop)
tocada 26 vezes
2
katy perry - california gurls (pop)
tocada 25 vezes
3
rihanna - rude boy (pop)
tocada 18 vezes
4
justin bieber - baby (pop)
tocada 16 vezes
5
katy perry - teenage dream (pop)
tocada 15 vezes
6
david guetta - sexy bitch (eletronica)
tocada 10 vezes
Genero mais frequente: pop
3
"calvin harris"
"how deep is your love"
"eletronica"
10
"maroon 5"
"animals"
"pop"
30
"calvin harris"
"feel so close"
"eletronica"
15
*/

```

```
/******************************************************************************
Defina um tipo estruturado para armazenar o nome e a idade de uma pessoa.

O seu programa deve ler um número n <= 30 e em seguida  ler as informações de n pessoas.
Você pode assumir que o nome de uma pessoa não possui espaços e tem no máximo 20 caracteres.

O seu programa deve ter uma função que recebe um vetor com as informações das pessoas, e o
número de elementos do vetor, e ordena as pessoas pelo nome. Caso duas pessoas possuam o mesmo nome,
ordene-as em ordem crescente de idade (uma pessoa mais nova deve vir antes de uma mais velha).

Ao final, na main ou em uma função específica, imprima a lista de pessoas ordenadas e quantas pessoas
são mais velhas do que a pessoa na última posição do vetor ordenado.
4
Bob 15
Alice 20
João 15
Alice 12

Os nomes São : Alice 12
Alice 20
Bob 15
João 15
1 pessoas mais velhas do que João
*******************************************************************************/

#include <iostream>
#include <cstring>
#define MAX_NOME 20
#define MAX 30

using namespace std;

struct Pessoa{
    char nomes[MAX_NOME];
    int idade;
};

void leNome(Pessoa p[], int n){
    cout << "Insira os nomes e idades: ";
    for(int i = 0;i < n;i++){
        cin >> p[i].nomes >> p[i].idade;
    }
}

void imprimeNome(Pessoa p[], int n){
    cout << "Os nomes São : ";
 	for(int i=0; i<n; i++){
 		cout << p[i].nomes << " " << p[i].idade << endl;
	 }
	    int cont = 0;
    for(int i = 0;i < n;i++){
        if(p[n-1].idade < p[i].idade){
            cont++;
        }
    }

       cout << cont << " pessoas mais velhas do que " << p[n-1].nomes << endl;
 }
void trocar(Pessoa &a, Pessoa &b){
    Pessoa aux;
    aux = a;
    a = b;
    b = aux;
}

void ordenarPeloNome(Pessoa p[MAX], int n){
    int ultimo = n -1;
    bool troca;

    do{
        troca = false;

        for(int j = 0;j < ultimo;j++){
            if(strcmp(p[j].nomes, p[j+1].nomes) > 0){
                troca = true;
                trocar(p[j], p[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}

void ordenarPelaIdade(Pessoa p[MAX], int n){
    int ultimo = n - 1;
    bool troca;
    do{
        troca = false;

        for(int j = 0 ;j < ultimo;j++){
            if(strcmp(p[j].nomes, p[j+1].nomes) == 0 && p[j].idade > p[j+1].idade){
                troca = true;
                trocar(p[j], p[j+1]);
            }
        }
        ultimo--;
    }while(troca == true);
}

int main()
{
    Pessoa p[MAX];
    int n;

    cout <<"Quantas Pessoais: ";
    cin >> n;

    leNome(p, n);
    imprimeNome(p, n);
    cout << "Ordenar pelo nome: ";
    ordenarPeloNome(p, n);
    imprimeNome(p, n);

    cout << "Ordenar pela idade: ";
    ordenarPelaIdade(p, n);
    imprimeNome(p, n);

    return 0;
}

```

# Escrevendo em um Arquivo

```
/*
Exemplo1: Escrever em um arquivo
=> Solicite ao usuário seu nome completo, sua idade e sua altura.
Ssalve estes dados em um arquivo de texto.
*/

#include <iostream>
#include <fstream>
#define MAX_NOME 30

using namespace std;

int main()
{

    char nome[MAX_NOME];
int idade;
float altura;

cout << "Informe seu nome completo: ";
cin.getline(nome, MAX_NOME);

cout << "Informe a idade e a altura: ";

cin >> idade >> altura;

char nomeArquivo[] = "meusDados.txt"; // usado para criar ou editar valores em um arquivo local no PC.

ofstream saida(nomeArquivo, ios::app); // comando usado para criar no disco um arquivo em branco

if(saida.is_open()){ // usado para testar se o arquivo foi criado e se foi apartir disso será escrito dentro dele.
	saida << nome << endl;
	saida << idade << endl;
	saida << altura << endl;
	saida.close(); // usado para fechar o arquivo.
}

    return 0;
}

```
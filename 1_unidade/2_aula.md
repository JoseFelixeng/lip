# Aula 2

- Variaveis
    - É um endereço na memoria do computador destinada a guarda uma determinada informação.
    - Toda variavel precisa ser declarada.
    - sempre ao final das linhas é necessario o uso do dois pontos.
    - Dentro de uma variavel só e possivel armazenar sem perda de informação variaveis do tipo selecionado.
    - Os caracteres selecionados no terminal, para serem salvos na memoria devem ser tomada a atenção pois será salvo apenas o primeiro caracter dependendo da variavel usada
- Variaveis e constantes
    - Variavel apos ser feita pode haver mudança no seu valor
    - constante: apartir do momento em que é feita a mesma não pode mudar o seu valor para utilizar usasse o Const
    - #define defini o valor da variavel antes da compilação, já o const só pode ser inserido uma vez .
- Expressões e Operadores
    - É através da construção de expressões que pode ser feita a transformação de variavel em informação.
    - Operadores Aritmeticos (+,-,*,/,% sendo que o resto da divisão não pode ser usado para entender numeros reais), além disso deve ser levado me consideração a precedencia do operador
        - Os Operadores Matematicos sempre tem maior precedencia, exceto quanto o operador é o de negação (!).
- Operador de Conversão Forçada (Casting)
    
    Utilizada para tratar uma variavel float como um valor inteiro.
    
    Ao colocar (int) antes da expressão como no exemplo dado na aula o numero decimal é forçado a se tornar um numero inteiro.
    
- Incremento e Decremento
    
    Significa soma um ou subtrair um de uma variavel qualquer que pode ser pré ou pós fixado.
    
    Quando um programa é feito com uma expressão e uma variado pos fixado o valor mudara apenas apos as alterações feitas nas expressões. Já se o operador é pre fixado o valor é extraido antes da equação ser feita
    
- Comando de seleção if
    
    Representação de como o if funciona
    
    Pode ser feita o encadeamento de "else if".
    

```
	# include <iostream>
	# include <cmath>

    using namespace std;

    int main() { float a, b, c, delta, x1 , x2;

    cout << "Informe os valores de a, b, c: ";

    cin >> a >> b >> c;

    delta = b*b - 4*a*c;

    if (delta < 0){
        cout << "Equação não existe raizes reais!" << endl;
    }else if(delta == 0){

        x1 = x2 = -b/(2*a);
        cout << "Raiz: " << x1 << endl;
    }else{
        x1 = (-b + sqrt(delta))/(2*a);
        x2 = (-b - sqrt(delta))/(2*a);

        cout << "x1: " << x1 << ", x2: " << x2 << endl;
    }

    return 0;

```

- Comando de Seleção Switch
    
    O break ao final do bloco indica o fim das intruções a serem executadas, caso não aja serão executados todos os itens abaixo.
    
    Tudo que pode ser feito com switch também da para ser feito com if, o inverso não é verdade.
    
    Outro exemplo offline
    
- O operador ternário(Comando de seleção)
    
    é usado para eliminar um bloco de if e else.
    
    Do ponto de vista computacional usa o operador ternario não faz diferença pois o computador irá fazer as mesmas atividades do cotidiano do app.
    
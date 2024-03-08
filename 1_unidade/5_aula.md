
# Aula 5

- O que é um processamento
    
    É uma função que não tem um valor de retorno ao final não haverá um valor que represente essa função
    
    A função do tipo void não tem um valor de retorno.
    
    O resultado de uma função do tipo void não pode ser atribuida a uma variavel.
    
- Passagem de parâmetros por valor e por referência
    - Por Valor
        - Função chamada recebe uma cópia do valor da variável usada como argumento na chamada da função:
        - Não tem acesso ao valor da variavel na chamada
    - Por Referência:
        - Função chamada recebe o endereço da variável usada como argumento na chamada da função:
        - Possui acesso ao valor da variavel durante a chamada;
    - ' & ' é o operador unario de referencia: sinalizar para uma função que ela irá receber uma copia do endereço informado.
- Funções que chamam funções
    
    Uma aspecto que exploramos pouco até o momento foi a capacidade de funções poderem chamar outras funções. Essa capacidade permite dividir uma tarefa em subtarefas, onde temos funções diferentes encarregadas de cada uma. Isto tem particular importância na modularização de problemas. Vamos adotar então o seguinte modelo de programação:
    
    - Cada função realiza uma tarefa específica do programa;
    - Se a função f pode realizar uma tarefa t , e a função g , para alcançar seu objetivo, precisa realizar t , então g vai chamar a função f .
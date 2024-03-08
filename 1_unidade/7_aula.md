## Aula 7 - Exercícios


```C++

# include<iostream>
#define MAX 30

using namespace std;

void leVetor(int v[], int n)
{
    for(int i = 0; i < n; i++)
    {
        cin >> v[i];
    }
}

void imprimeVetor(int v[], int n)
{
    for (int i = 0; i < n; i++)
    {
        cout << v[i] << endl;
    }
}

void troca (int &x, int &y)
{
    int aux = x;
    x = y;
    y = aux;
}

void ordenaCrescente (int v[], int n) // BubbleSort
{
    int ultimo = n-1;
    bool trocou = true;

    do {

        trocou = false;

        for (int i = 0; i < n; i++)
        {
            if(v[i] > v[i+1])
            {
                troca(v[i], v[i+1]);
                trocou = true;
            }
        }
        ultimo--;
    }while (trocou == true);

}

 ordenaDecrescente (int v[MAX], int n)
 {
    int ultimo = n-1;
    bool trocou = true;

    do {

        trocou = false;

        for (int i = 0; i < n; i++)
        {
            if(v[i] < v[i+1])
            {
                troca(v[i], v[i+1]);
                trocou = true;
            }
        }
        ultimo--;
    }while (trocou == true);

}



void ordenar(int v[], int n)
{
    int vPares[MAX];
    int vImpares[MAX];

    int nPares = 0, nImpares = 0;
    for(int i = 0; i < n;i++){
        if(i % 2 == 0)
        {
            vPares[nPares] = v[i];
            nPares++;
        }
        else
        {
            vImpares[nImpares] = v[i];
            nImpares++;
        }

    }

    cout << "Elementos nos índices pares: ";
    imprimeVetor(vPares, nPares);
    imprimeVetor(vImpares, nImpares);
    ordenaCrescente (vPares,nPares);


    cout << "Depois de ordenar" << endl;
    cout << "Elementos nos índices pares: ";
    imprimeVetor(vPares, nPares);

    cout << "Elementos nos índices ímpares: ";

    imprimeVetor(vImpares, nImpares);

    ordenaDecrescente (vImpares, nImpares);
}

int main()
{
    int n;
    int v[MAX];
    cin >> n;

    leVetor(v, n);
    ordenar(v, n);

}
```
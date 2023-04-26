# MatiasGil2002.github.io
Matias Gil
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h>
#include "pila.h"
#include <time.h>

///Prototipados.
void menuOpciones();
int cargaArreglo(int arreglo[],int v, int d);
void mostrarArreglo(int a[],int v);
int sumaElementos(int a[],int v);
void arregloPila(int a[],int v,Pila dada);
int cargaArregloReal(float a[],int v,int dim);
void mostrarFlotante(float a[],int v);

int main()
{
    int opcion;
    int a[50];
    int validos=0;
    int dim =50;
    int sumar=0;
    Pila dada;
    inicpila(&dada);
    float arregloF[50];

    do
    {
        menuOpciones();
        scanf("%d",&opcion);
        switch(opcion)
        {
        case 1:
            validos=cargaArreglo(a,validos,dim);
            break;
        case 2:
            mostrarArreglo(a,validos);
            break;
        case 3:
            sumar=sumaElementos(a,validos);
            printf("\nEl resultado de la suma es: %d\n",sumar);
            break;
        case 4:
            arregloPila(a,validos,dada);
            break;
        case 5:
            validos=cargaArregloReal(arregloF,validos,dim);
            mostrarFlotante(arregloF,validos);
            printf("\n");
            break;
        }
        system("pause");
        system("cls");
    }
    while(opcion>0 && opcion<=9);
    return 0;
}
///Funcion que carga un arreglo:
int cargaArreglo(int arreglo[],int v, int d)
{
    char opcion='s';

    while(opcion=='s')
    {
        printf("\nIngrese un elemento al arreglo: \n");
        scanf("%d",&arreglo[v]);

        printf("\nDesea seguir ingresando elementos al arreglo? .<s/n>.\n");
        fflush(stdin);
        opcion=getch();
        v++;
    }
    return v;
}
///Funcion que muestra un arreglo:
void mostrarArreglo(int a[],int v)
{
    int i;

    printf("\nMostrando el arreglo: \n");
    for(i=0; i<v; i++)
    {
        printf("\t%d -\n",a[i]);
    }
}
///Suma de los elementos del arreglo:
int sumaElementos(int a[],int v)
{
    int acum=0;

    for(int i=0; i<v; i++)
    {
        printf("%d - ",a[i]);
        acum=acum+a[i];
    }
    return acum;
}
///De arreglo a pila:
void arregloPila(int arreglo[],int v,Pila dada)
{
    int i;
    for(i=0; i<v ; i++)
    {
        apilar(&dada,arreglo[i]);
    }
    printf("\nElementos del arreglo pasados a la Pila: \n");
    mostrar(&dada);
}
///Carga un arreglo de numeros flotantes:
int cargaArregloReal(float a[],int v,int dim)
{
    srand(time(0));

    for(v=0;v<dim;v++)
    {
        a[v] = (float) ((rand()%100)/((100/10)+0.1));
    }
    return v;
}
///Mostrar un arreglo de flotantes:
void mostrarFlotante(float a[],int v)
{
    float acum=0;
    int i;
    for(i=0;i<v;i++)
    {
        printf("%.2f - ",a[i]);
        acum=acum+a[i];
    }
    printf("\nLa suma de los elementos del arreglo flotante es: %.2f\n",acum);
}
///Menu que muestra las opciones disponibles:
void menuOpciones()
{
    printf("\n\n");
    printf("1- Cargar arreglo por teclado.\n");
    printf("2- Mostrar arreglo ya cargado.\n");
    printf("3- Sumar elementos del arreglo.\n");
    printf("4- Pasar elementos de arreglo a pila.\n");
    printf("5- Suma flotantes.\n");
    printf("6- Encontrar elemento de tipo char dentro de un arreglo.\n");
}

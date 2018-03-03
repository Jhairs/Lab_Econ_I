# **Notas de primera sesión de R.**

## **_Sobre la estructura básica para usar Markdown._**

En esta parte del laboratorio mediante el uso del archivo "temprale", elaborado por el laboratorista asignado, se explicó la manera de llevar a cabo escritura en el programa en cuestión. De forma general se abordó:

1. Como poner titulos y poner el texto en negritas y cursivas.
2. Como realizar listas.
3. Como meter links dentro del escrito e imagenes.

## **_Breve introducción a R-Studio y el uso en el álgebra matricial._**

### _Elementos básicos_

A modo de introducción se mencionaron los elementos más destacados de R (como lo es su diversidad de aplicación y su condición de software libre) y se mencionó el porque es hoy en día uno de los más implementados, siendo su libre acceso una de sus principales virtudes.

Posteriormente, se mostró como saber en donde define R nuesto espacio de trabajo y como poder cambiarlo. Ello usando los comandos getwd() para saber donde esta trabajando el programa y setwd() para re-definir ese espacio de trabajo.

Definido el espacio de trabajo se menciono la utilidad del programa para hacer operaciones algebraicas y algunas otras más complejas; además se mostró como asignar valores a un objeto, donde se utiliza el signo igual y si se asigna un caracter, este se debe entre comillar. 
Ejemplo:

    X=sqrt(0) 
    A= "Acoso"

    class(A)
    class(X)

Debido a que los elementos ingresados en R pueden ser variados, se utilizo la función class() para conocer su naturaleza.

    class(A)
    class(X) 

Como se mostró en clase, una vez definidos los elementos (por ejemplo, X y A) estos se pueden llamar (utilizar) en cualquier momento y si se vuelven a definir estos cambian al valor más nuevo.

### _Elaboración de vectores, matrices y operaciones básicas entre ellos._

Para crear vectores se siguió el procedimiento siguiente:

    c(1,2,3,4)

Y definiendolos como una variable (es decir, x=c(...)) se pueden realizar operaciones con ellos.

    a=c(1,2,3,4)
    b=c(5,6,7,8)

    a-b.......Resta de vectores
    a+b.......Suma de vectores
    a<b.......Prueba lógica con vectores
    
Por otra parte para elaborar matrices en el programa se hace uso de la función =matrix(c(...),a), donde el primer algumento se usa para definir un vector con k elementos y el segundo termino corresponde a el número de columnas en las que se separara el vector.

    A=matrix(c(1,2,3,4,5,6),2)

         [,1] [,2] [,3]
    [1,]    1    3    5
    [2,]    2    4    6

De otra manera, si se usa la expresión a:b se generan tantos elementos enteros como la distancia de b-a, dado que el programa acomoda los elemntos por columna al usar byrow=T o byrow=F, se acomodan los elemntos por columna o hilera respectivamente.

    B=matrix(1:9, byrow= F, nrow=3)

        [,1] [,2] [,3]
    [1,]    1    4    7
    [2,]    2    5    8
    [3,]    3    6    9

La transpuesta de matrices:

    t(A)
         [,1] [,2]
    [1,]    1    2
    [2,]    3    4
    [3,]    5    6

La multiplicación de matrices:

    A%*%B
         [,1] [,2] [,3]
    [1,]   22   49   76
    [2,]   28   64  100

La inversa de matrices:

    C=matrix(c(1,2,3,4,5,6,12,11,0),3)
    solve(C)

        [,1] [,2]       [,3]
    [1,] -2.2  2.4 -0.5333333
    [2,]  1.1 -1.2  0.4333333
    [3,] -0.1  0.2 -0.1000000

Se mostró como seleccionar elementos de una matriz mediante el comando A[a], donde A es la matriz y a el elemento que se requiere. De forma identica se mostró como obtener la hilera a de una matriz A[a,] o la columna a de una matriz A[,a].
Para definir nuevos elementos o hileras o columnas de una matriz se redefinian los elementos de la siguiente manera:

    > A
         [,1] [,2] [,3]
    [1,]    1    3    5
    [2,]    2    4    6

    > A[4]=100
    > A
         [,1] [,2] [,3]
    [1,]    1    3    5
    [2,]    2  100    6

    > A[1,]=c(200,300,400)
    > A
         [,1] [,2] [,3]
    [1,]  200  300  400
    [2,]    2  100    6

###_Aplicación a ejercicio 4 de tarea 1._

1. Pasando los datos dados en el ejercicio;

    _Esperanzas de X_
        Ex1=0
        Ex2=-4
        Ex3=1
    _Esperanzas de Y_
        Ey1=-1
        Ey2=4
    _Varianzas de X_
        Vx1=1
        Vx2=4
        Vx3=2
    _Varianzas de Y_
        Vy1=1
        Vy2=9
    _Covarianzas de X1_
        Cx1x2=-1
        Cx1x3=0
        Cx1y1=0
        Cx1y2=1
    _Covarianzas de X2_
        Cx2x3=2
        Cx2y1=-1
        Cx2y2=-3
    _Covarianzas de X3_
        Cx3y1=0
        Cx3y2=3
    _Covarianzas de Y_
        Cy1y2=-2

2. Resultados.

    i) 
        EX=matrix(c(Ex1,Ex2,Ex3),3)
             [,1]
        [1,]    0
        [2,]   -4
        [3,]    1

        VX=matrix(c(Vx1,Cx1x2,Cx1x3,Cx1x2,Vx2,Cx2x3,Cx1x3,Cx2x3,Vx3),byrow=T,nrow=3)
             [,1] [,2] [,3]
        [1,]    1   -1    0
        [2,]   -1    4    2
        [3,]    0    2    2

        EY=matrix(c(Ey1,Ey2),2)
             [,1]
        [1,]   -1
        [2,]    4

        VY=matrix(c(Vy1,Cy1y2,Cy1y2,Vy2),byrow=T,nrow=2)
             [,1] [,2]
        [1,]    1   -2
        [2,]   -2    9

        CXY=matrix(c(Cx1y1,Cx1y2,Cx2y1,Cx2y2,Cx3y1,Cx3y2),byrow=T,nrow=3)
             [,1] [,2]
        [1,]    0    1
        [2,]   -1   -3
        [3,]    0    3

        CYX=t(CXY)
             [,1] [,2] [,3]
        [1,]    0   -1    0
        [2,]    1   -3    3


    ii) Calcular la esperanza y varianza de -1X1 + 3/2X2 - 4X3

        a=matrix(c(-1, 3/2,-4),1)

        EaX=a%*%EX
             [,1]
        [1,]  -10

        VaX= a%*%VX%*%t(a)
             [,1]
        [1,]   21
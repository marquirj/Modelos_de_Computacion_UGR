# Prácticas para la asignatura MODELOS DE COMPUTACIÓN.  

## Realizado por Juan Antonio Martín Quirós.



## Práctica 1. Determinar si la gramática G =( {S,A,B}, <{a,b,c,d}, P ,S) donde P es el conjunto de reglas de producción.

## S -> AB , A -> Ab , A -> a , B -> cB , B -> d

## genera un lenguaje de tipo 3.

Esta gramática genera el lenguaje: {ab^ic^jd: i, € |N } y este lenguaje se puede generar.

S -> ab, B -> bB, B -> C, C-> cC, C -> d.

Como esta gramática es de tipo 3, el lenguaje lo es.








## Práctica 2.
## Apartado a. Convertir un Autómata Finito No Determinista a un Autómata Finito Determinista. Una vez convertido debemos minimizarlo. Con transiciones vacías. Práctica realizada con JFLAP.

- Autómata Finito No Determinista con transiciones vacías.
![AFND](/img/AFND.jpg)
- Autómata Finito Determinista.
![AFD](/img/AFD.jpg)
- Autómata Finito Determinista minimizado.
![AFDMin](/img/AFDMin.jpg)

## Apartado b. Convertir un Autómata Finito No Determinista a un Autómata Finito Determinista. Una vez convertido debemos minimizarlo. Sin transiciones vacías. Práctica realizada con JFLAP.

- Autómata Finito No Determinista
![AFND](/img/AFNDS.jpg)
- Autómata Finito Determinista.
![AFD](/img/AFDS.png)
- Autómata Finito Determinista minimizado.
![AFDMin](/img/AFDSMin.png)

## Práctica 3.
## Uso de Lex y Jacc. (contenido en las transparencias del profesor)

Se da un archivo llamado ejemplo, con el siguiente contenido:

car	[a-zA-Z]  
digito	[0-9]  
signo	(\-|\+)  
suc	({digito}+)  
enter	({signo}?{suc})  
real1	({enter}\.{digito}*)  
real2	({signo}?\.{suc})  
	int ent=0, real=0, ident=0, sumaent=0, i=0;  
%%  

{enter} {  
	ent++;  
	 sscanf(yytext,"%d",&i);  
	 sumaent = sumaent +i;  
}  


({real1}|{real2})  
{  
real++; printf("Num. real%s\n", yytext);  
}  
{car}({car}|{digito})*  
{ident++; printf("Var. ident.%s\n", yytext);  
}  
.|n	{;}  

%%  

int yywrap(){  
printf("NUMERO de Enteros%d, reales%d, ident%d, Suma de Enteros%d", ent, real, ident,   sumaent);  
return 1;  
}  

Para ejercutar ese fichero con lex se ejecuta en el terminal lo siguiente:
- lex ejemplo

Despues se compila el archivo generado por lex con la siguiente orden:
- gcc lex.yy.c -o prog -ll

Por último se crea un archivo con varios números que se llamará entrada.in con el siguiente contenido:  

1  
1  
3  
2.5  
+5  
2.5  
10  
12.5  

Por último se ejecutará el progama resultante de la siguiente manera:  
- ./prog < entrada.in > salida.out  

El resutado del programa sería:  

![salida](/img/jj.png)


# Práctica 4

## Realizar un autómata con pila. Transparencia 29 tema 5

M = ({q1,0,R},{0,1},{R,X}, δ, q1,R,conjunto vacio), el lenguaje L= {0i1j .i >=j>=0}

δ(q1,0,R )= {(q1,XR)}  δ(q1,0,X ) = {(q1,XX)}
δ(q1,ε,R )= {(q1,ε)}  δ(q1,1,X ) = {(q2,ε)}
δ(q2,1,X )= {(q2,ε)}  δ(q2,ε,R ) = {(q2,ε)}
δ(q2,ε,X ) = {(q2,ε)}

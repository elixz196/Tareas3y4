# 3 Herencia.

##  1.  Define: Clase Base, Clase Derivada.

=============================================================

**Clase base**: Una clase base es aquella que no dependen ninguno de sus atributos u objetos de la clase de alguna otra clase, se podría decir que en términos de herencia, seria la clase padre, la clase que se mantiene fija, en el aspecto de herencia.
Es también por así llamarlo la clase principal de un programa, seria la clase primaria sin incluir la clase main en donde se corre todo el programa en si.

**Clase derivada**: Son clases que dependen de las clases bases, ya que algunos de sus métodos son también heredados, y muchas veces, el compilador arrojara malos resultados, ya que al ser dependientes estas clases, a veces podrán generar errores lógicos.

=============================================================

##  2.  Haz un diagrama UML donde se muestre la relación de herencia entre las  clases Figura, Recangulo y Circulo como vimos en clase.

![Digrama UML](https://github.com/elixz196/Tareas3y4/blob/master/Fotos/Diagrama.PNG "Este es el diagrama")

## 3. ¿ Indica cuales son las clases base y las derivadas.

**Base:** la clase base es la clase padre osea la principal

**Derivada:** la clase derivada es la que obtiene los parametros de la clase base por herencia.

## 4. ¿Que es herencia simple y herencia múltiple? ¿En c# se puede hacer herencia múltiple?

**Herencia simple**: indica que se pueden definir nuevas clases solamente a partir de una clase inicial

**Herencia multiple**: indica que se pueden definir nuevas clases a partir de dos o más clases iniciales.

java solo permite herencia simple, al igual que c#.

## 5. Escribe el programa de Figura como vimos en clase, donde agregues varios tipos de figuras a una lista y recorre la lista llamando a un metodo de las figuras, además :
### 5.1 Se sobrecarguen los constructores y se acceda a los constructores de la clase base

    using System;
    using System.Collections.Generic;

    namespace Figura2
    {
    class Vector2d
    {
        public int x, y;
        public Vector2d(int x, int y)
        {
            this.x=x; this.y=y;
        }
        public override string ToString()
        {
            return String.Format("{0},{1}", x, y);
        }
    }
    abstract class Figura
    {
        public Vector2d position;
        public string fill ,border;

          //Constructor por defecto 
        public Figura():this( new Vector2d(100, 100))
        {
        
        }
        //constructor de figura
        public Figura(Vector2d pos)
        {
            position= pos;
            fill= "white";
            border= "black";
        }

        public abstract void Dibuja();
    }

    class Circulo : Figura
    {
     private int radio;
     public Circulo(Vector2d pos, int radio):base(pos)
     {
         this.radio= radio;
     }
     public Circulo ():base()
     {
         this.radio= 10;
     }

     public override void Dibuja() 
     {
         Console.WriteLine("Se dibuja un circulo en {0} de color {1}", position, fill);
     }
    }
 
    class Rectangulo : Figura
    {
     
     public Rectangulo(Vector2d pos):base(pos)
     {
         
     }
     public Rectangulo ():base()
     {
        
     }

     public override void Dibuja() 
     {
         Console.WriteLine("Se dibuja un Rectangulo en {0} de color {1}", position, fill);
     }
    }

     class Triangulo : Figura
     {
         private int lados;
         public Triangulo(Vector2d pos, int numlados):base(pos)
         {
             lados=numlados;
         }
        public Triangulo ():base()
        {
        
        }

        public override void Dibuja() 
         {
         Console.WriteLine("Se dibuja un Triangulo en {0} de color {1} lados {2}", position, fill, lados);
        }
     }
    class Cuadrado : Figura
    {

        private int lados;
         public Cuadrado(Vector2d pos):base(pos)
         {
             lados=4;
         }
        public Cuadrado():base()
        {
        
        }

        public override void Dibuja() 
         {
         Console.WriteLine("Se dibuja un cuadrado en {0} de color {1} lados {2}" , position, fill,lados);
        }
    
    }
    class Program
    {
        static void Main(string[] args)
        {

            List<Figura> figuras = new List<Figura>();
            figuras.Add(new Circulo());
            figuras.Add(new Rectangulo(new Vector2d(200,200)));
            figuras.Add(new Triangulo(new Vector2d(200,320),3));
            figuras.Add(new Cuadrado(new Vector2d(239,224)));
            foreach(Figura f in figuras)
            f.Dibuja();
           
        }
    }
}
### 5.2 Explica para que nos sirve la palabra base:
La palabra base nos sirve para expresar que la clase derivada va a recibir los atributos de la clase padre(base)

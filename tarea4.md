# 1. Considera el siguiente fragmento de programa:

using System;

class A

    {

    public int a;

    public A()

        {

        a = 10;

        }

    public _______ string Display()

      {

      return a.ToString();

      }

    }

class B:A

   {

   public int b;

   public B():base()

   {

    b = 15;

   }

 

  // #########################################

  //  #Después de contestar la pregunta 1                  

 //   #Redefine el método Display( ) en este espacio,  debe regresar el campo b como string.

 //  #########################################

 

}

 class Program

  {

   public static void Main()

   {

  A objA = new A();

  B objB = new B();

  Console.WriteLine(objA.Display()); ////  (1 )

  Console. WriteLine(objB.Display()); ////  ( 2)

  }

  }

## 1.1. ¿Qué valores imprimen las lineas (1) y (2) ?

10 y 10

## 1.2.  Redefine el método Display en el espacio indicado,

  using System;

  namespace tarea4
 {


    class A

   {

      public int a;

      public A()

      {

          a = 10;

      }

      public virtual  string Display()

      {

        return a.ToString();

      }

  }

  class B : A

  {

      public int b;

      public B() : base()

      {

        b = 15;

      }



    public override string Display()

     {

        return b.ToString();

     }


 }

 class Program

 {

    static void Main(string[] args)

    {

        A objA = new A();

        B objB = new B();

        Console.WriteLine(objA.Display()); ////  (1 )

        Console.WriteLine(objB.Display()); ////  ( 2)

        Console.ReadKey();
        

    }

  }

 }

### una vez redefinido el método, ¿qué valores imprimen las lineas (1) y (2) ?.
     
     10 y 15

## 1.3. ¿Que palabra debes agregar en la linea (public _______ string Display()) al definir A.Display()?

se debe agregar virtual

# 2. Considera el siguiente fragmento de programa:

using System;

using System.Collections.Generic;

 ________ class Musico

    {

    public string nombre;

    public Musico (string n)

        {

         nombre = n;

        }

   public abstract (A) void Afina();  (B)

   public (C) string Display()

      { 

       return nombre;

      }

   }

class Bajista; Musico

  {

    public string instrumento;

    public Bajista (string n, string i ) ......

    .........

    public _________ Afina()

      {

      ________________

      }

 }

class Guitarrista ____________

     {

     public instrumento;

      // Falta el constructor y otras cosas??

 

     }

 

class Program

 {

  public static Main()

   {

  Musico musico = new Musico("Django"); (D)

  Bajista b = new Bajista("Flea");

  Guitarrista g = new Guitarrista("Santana");

  List<Musico> musicos = ____________________

  musicos.Add( b);

  musicos.Add(g);

 

  foreach ( _____in musicos______)

        ____________________

 // (m as IAfina).Afina()

 Console.ReadKey();

  

 }

}

## 2.1. Completa el programa.

    using System;
using System.Collections.Generic;


interface IAfina
    {
        void Afina();
    }

    class Musico : IAfina
    {
        public string nombre;
        public Musico(string n)
        {
            nombre = n;
        }

        public void Afina()
        {
            Console.WriteLine("Musico Está afinado");
        }

        public override string ToString ()
        {
            return string.Format("Nombre: {0}", nombre);
        }
}

    class Bajista : Musico,IAfina
    {
        public string instrumento;
        public Bajista(string n, string i) : base(n)
        {
            instrumento=i;
        }
        public virtual new void Afina()
        {
            Console.WriteLine("El bajista está afinado");
        }
        public override string ToString ()
        {
            return string.Format("Nombre: {0},{1} ", nombre,instrumento);
        }
    }

    class Guitarrista : Musico,IAfina
    {
        public string instrumento;
        public Guitarrista(string n, string i): base (n)
        {
            instrumento = i;
        }

        public virtual new void Afina()
        {
            Console.WriteLine("El guitarrista está afinado");
        }

        public override string ToString()
        {
            return string.Format("Nombre: {0},{1} ", nombre, instrumento);
        }
}

    class Program
    {
        static void Main(string[] args)
    {
        Musico m = new Musico("Django"); 
        Bajista b = new Bajista("carlos","bajista");
        Guitarrista g = new Guitarrista("roberto","Guitarrista");

        List<Musico> musicos = new List<Musico>();
        musicos.Add(b);
        musicos.Add(g);
        musicos.Add(m);

        foreach (Musico mu in musicos)
        {
            (b as IAfina).Afina();
            (g as IAfina).Afina();
            (m as Musico).Afina();
            Console.WriteLine(mu);
        }
        Console.ReadKey();
}

}

## 2.2. Hay un error en uno de los puntos (A)(B)(C)(D). ¿Cuál es y por qué?
(A) no hay error
(B) No debe llevar punto y coma
(C) Se debe redefinir
(D) no hay errores, esta bien creado el objeto.

## 2.3. ¿Qué método se debe implementar obligatoriamente en ambas clases y por qué?

El metodo afina() porque viene de clase abstracta.

## 2.4. ¿Por qué no se ponen las llaves en (B)?, ¿Cuando si se pondrían?

porque no esta redefiniendo

## 2.5. ¿Qué pasa si el método Afina() lo hacemos virtual en lugar de abstract?

No se podria implementar en todo

# 3. Implementa el programa utilizando interfaces en lugar de herencia.

using System;
using System.Collections.Generic;


interface IAfina
    {
        void Afina();
    }

    class Musico : IAfina
    {
        public string nombre;
        public Musico(string n)
        {
            nombre = n;
        }

        public void Afina()
        {
            Console.WriteLine("Musico Está afinado");
        }

        public override string ToString ()
        {
            return string.Format("Nombre: {0}", nombre);
        }
}

    class Bajista : Musico,IAfina
    {
        public string instrumento;
        public Bajista(string n, string i) : base(n)
        {
            instrumento=i;
        }
        public virtual new void Afina()
        {
            Console.WriteLine("El bajista está afinado");
        }
        public override string ToString ()
        {
            return string.Format("Nombre: {0},{1} ", nombre,instrumento);
        }
    }

    class Guitarrista : Musico,IAfina
    {
        public string instrumento;
        public Guitarrista(string n, string i): base (n)
        {
            instrumento = i;
        }

        public virtual new void Afina()
        {
            Console.WriteLine("El guitarrista está afinado");
        }

        public override string ToString()
        {
            return string.Format("Nombre: {0},{1} ", nombre, instrumento);
        }
}

    class Program
    {
        static void Main(string[] args)
    {
        Musico m = new Musico("Django"); 
        Bajista b = new Bajista("carlos","bajista");
        Guitarrista g = new Guitarrista("roberto","Guitarrista");

        List<Musico> musicos = new List<Musico>();
        musicos.Add(b);
        musicos.Add(g);
        musicos.Add(m);

        foreach (Musico mu in musicos)
        {
            (b as IAfina).Afina();
            (g as IAfina).Afina();
            (m as Musico).Afina();
            Console.WriteLine(mu);
        }
        Console.ReadKey();
}

}

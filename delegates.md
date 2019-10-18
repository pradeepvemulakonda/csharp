 ```csharp
 using System;

class MainClass {

  private string name = "MainClass";

  public static void Main (string[] args) {
    Console.WriteLine ("Hello World");
    OneStringDelegate name = printName;
    OneStringDelegate hello = printHello;
    name("Test");
    hello("world");
    MainClass mainClass = new MainClass();
    mainClass.callsSecond();
    OneStringDelegate name1 = new OneStringDelegate(printName);
    OneStringDelegate hello1 = new OneStringDelegate(printHello);
    OneStringDelegate nc;
    nc = name1;
    nc +=hello1;
    nc("BumBum");
    
  }

  private void callsSecond() {
    SecondClass secClass = new SecondClass();
    secClass.Print(this.Grunt);
  }

  public delegate void OneStringDelegate(string input);

  public static void printName(string input) {
    Console.WriteLine ($"Name {input}");
  }

   public static void printHello(string input) {
    Console.WriteLine ($"Hello {input}");
  }

  public void Grunt() {
    Console.WriteLine ($"grunt {this.name}");
  }
}

class SecondClass {
  public delegate void Del();

  public void Print(Del delegate1) {
    delegate1();
  }
}
 
```

---
title: "Wyrażenia lambda (Przewodnik programowania w języku C#)"
ms.date: 03/03/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 14bb60a5009f9a1ae59ed9846ebc868cfdcc05c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="lambda-expressions-c-programming-guide"></a>Wyrażenia lambda (Przewodnik programowania w języku C#)
Wyrażenie lambda jest [funkcji anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) używanej do tworzenia [delegaty](../../../csharp/programming-guide/delegates/using-delegates.md) lub [drzewo wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) typów. Za pomocą wyrażenia lambda można pisać funkcje lokalne, które mogą być przekazywane jako argumenty lub zwracane jako wartość wywołania funkcji. Wyrażenia lambda są szczególnie przydatne w przypadku pisania wyrażeń zapytań w języku LINQ.  
  
 Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda [ => ](../../../csharp/language-reference/operators/lambda-operator.md), i umieszcza blok wyrażenia lub instrukcji z drugiej strony. Na przykład, wyrażenie lambda `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów. To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 Aby utworzyć typ drzewa wyrażeń:  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 `=>` Operator ma takie samo pierwszeństwo jako przypisania (`=`) i jest [prawo asocjacyjnej](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (zobacz sekcję "Kojarzenie" w artykule operatory).  
  
 Wyrażenia lambda są używane w oparte na metodzie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wysyła zapytanie jako argumenty do metod operator standardowej kwerendy, takich jak <xref:System.Linq.Enumerable.Where%2A>.  
  
 Jeśli używasz składni na podstawie metody do wywołania <xref:System.Linq.Enumerable.Where%2A> metody w <xref:System.Linq.Enumerable> klasy (tak jak w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) parametr jest typem obiektu delegowanego <xref:System.Func%602?displayProperty=nameWithType>. Użycie wyrażenia lambda jest najwygodniejszym sposobem tworzenia delegata. Podczas wywoływania tej samej metody, na przykład <xref:System.Linq.Queryable?displayProperty=nameWithType> klasy (tak jak w [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), a następnie typ parametru jest <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> Func w przypadku dowolnego delegatów Func o do szesnastu parametrów wejściowych. I znowu wyrażenie lambda jest tylko bardzo zwięzłym sposobem konstruowania takiego drzewa wyrażeń. Zezwalaj na wyrażeń lambda `Where` wywołań wyglądać podobnie, chociaż w rzeczywistości różni się typ obiektu utworzone na podstawie lambda.  
  
 W poprzednim przykładzie parametr typu wejściowy powiadomienie, że podpis delegata ma jedną niejawnie wpisanych `int`i zwraca `int`. Wyrażenia lambda można przekonwertować na delegata tego typu, ponieważ obejmuje ona również jeden parametr wejściowy (`x`) i które kompilator niejawnie przekonwertować na typ wartości zwracanej `int`. (Wnioskowanie typów omówiono bardziej szczegółowo w następnych sekcjach). Kiedy delegat jest wywołany za pomocą parametru wejściowego 5, zwraca wynik 25.  
  
 Wyrażenia lambda nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) lub [jako](../../../csharp/language-reference/keywords/as.md) operatora.  
  
 Wszystkie ograniczenia, które dotyczą metod anonimowych, dotyczą także wyrażeń lambda. Aby uzyskać więcej informacji, zobacz [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## <a name="expression-lambdas"></a>Lambdy wyrażeń  
 Wyrażenia lambda za pomocą wyrażenia po prawej stronie = > — operator jest wywoływana *wyrażenia lambda*. Wyrażenia lambda są często używane w konstrukcji [drzew wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:  
  
```csharp
(input-parameters) => expression
```

 Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane. Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:  
  
```csharp
(x, y) => x == y
```

 Czasami wywnioskowanie typów wejściowych jest dla kompilatora trudne lub wręcz niemożliwe. W takiej sytuacji można jawnie określić typy, tak jak pokazano w poniższym przykładzie:  
  
```csharp
(int x, string s) => s.Length > x
```

 Określanie braku parametrów wejściowych za pomocą pustych nawiasów:  
  
```csharp
() => SomeMethod()
```

 Należy zauważyć, że w poprzednim przykładzie treść wyrażenia lambda może składać się z wywołania metody. Jednak w przypadku tworzenia drzew wyrażeń, które będą obliczane poza programem .NET Framework, na przykład w programie SQL Server, nie należy używać wywołań metod w wyrażeniach lambda. Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.  
  
## <a name="statement-lambdas"></a>Lambdy instrukcji  
 Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:  
  
(parametry wejściowe) = > {instrukcja;}

 Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.  
  
## <a name="async-lambdas"></a>Lambdy asynchroniczne  
 Można jednak łatwo tworzyć wyrażenia lambda i instrukcje zawierające przetwarzania asynchronicznego przy użyciu [async](../../../csharp/language-reference/keywords/async.md) i [await](../../../csharp/language-reference/keywords/await.md) słów kluczowych. Na przykład w poniższym przykładzie formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje i oczekujące na metody asynchronicznej `ExampleMethodAsync`.  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej. Aby dodać ten program obsługi, Dodaj `async` modyfikator przed listy parametrów lambda, jak przedstawiono na poniższym przykładzie.  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 Aby uzyskać więcej informacji o sposobie tworzenia i używania metody asynchroniczne, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md).  
  
## <a name="lambdas-with-the-standard-query-operators"></a>Lambdy ze standardowymi operatorami zapytań  
 Wiele standardowych operatorów zapytań ma parametr wejściowy, którego typ jest jednym z <xref:System.Func%602> rodzina delegatów. Te delegaty używają parametrów typu użycia, aby zdefiniować liczbę i typy parametrów wejściowych oraz zwracany typ delegata. `Func` Obiekty delegowane są bardzo przydatne w przypadku hermetyzując wyrażenia zdefiniowane przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Na przykład rozważmy następujący typ delegata:  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 Delegat można wdrożyć jako `Func<int,bool> myFunc` gdzie `int` jest parametrem wejściowym i `bool` jest zwracana wartość. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. `Func<int, string, bool>` Definiuje delegata z dwóch parametrów wejściowych, `int` i `string`i typ zwracany `bool`. Następujące `Func` delegata, gdy jest wywoływana, zwraca wartość PRAWDA lub FAŁSZ, aby wskazać, czy parametr wejściowy jest równa 5:  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Może też podawać wyrażenia lambda, gdy typ argumentu jest `Expression<Func>`, na przykład w przypadku standardowych operatorów zapytań zdefiniowane w System.Linq.Queryable. Po określeniu `Expression<Func>` argument, wyrażenie lambda zostanie skompilowany na drzewo wyrażenia.  
  
 Operator zapytania standardowe <xref:System.Linq.Enumerable.Count%2A> metody, jest następujący:  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To wyrażenie lambda określonej liczby tych liczb całkowitych (`n`) który podzielona przez dwa mieć reszty 1.  
  
 Następujący wiersz kodu tworzy sekwencję, który zawiera wszystkie elementy w `numbers` tablicy, które są do lewej strony 9, ponieważ jest to pierwszy numer w sekwencji, które nie spełniają warunek:  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 W tym przykładzie pokazano, jak określić wiele parametrów danych wejściowych, umieszczając je w nawiasach. Metoda zwraca wszystkie elementy w tablicy liczb, dopóki nie napotka liczby, której wartość jest mniejsza niż jej pozycja. Nie należy mylić operatora lambda (`=>`) z operatorem większe lub równe (`>=`).  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>Wnioskowanie typów w wyrażeniach lambda  
 Podczas pisania wyrażeń lambda często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ na podstawie treści wyrażenia lambda, typu delegata parametru i innych czynników, tak jak opisano w specyfikacji języka C#. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Tak, wyszukując `IEnumerable<Customer>`, następnie wejściowego zmiennej jest wywnioskowany jako `Customer` obiektu, co oznacza, że masz dostęp do właściwości i metod:  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 Ogólne reguły dotyczące wyrażeń lambda są następujące:  
  
-   Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.  
  
-   Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.  
  
-   Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.  
  
 Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie obejmuje wewnętrznej koncepcji „wyrażenia lambda”. Jednak czasami wygodnie jest mówić potocznie o „typie” wyrażenia lambda. W takich przypadkach typ odwołuje się do typu delegata lub <xref:System.Linq.Expressions.Expression> wpisz jest konwertowane Wyrażenie lambda.  
  
## <a name="variable-scope-in-lambda-expressions"></a>Zakres zmiennych w wyrażeniach lambda  
 Wyrażenia lambda, może się odwoływać do *zmienne zewnętrzne* (zobacz [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) w zakresie w metodę, która definiuje funkcję lambda, lub w zakresie w typie, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano te reguły:  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:  
  
-   Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.  
  
-   Zmienne zawarte w wyrażeniu lambda nie są widoczne w metodzie zewnętrznej.  
  
-   Wyrażenia lambda nie może bezpośrednio przechwytywania `in`, `ref`, lub `out` parametru z metody otaczającej.  
  
-   Instrukcja return w wyrażeniu lambda nie powoduje wykonania instrukcji return w otaczającej go metodzie.  
  
-   Wyrażenia lambda nie może zawierać `goto` instrukcji, `break` instrukcji lub `continue` instrukcji, która znajduje się wewnątrz funkcji lambda w przypadku docelowej instrukcji skok poza blokiem. Błędem jest również instrukcja skoku poza blok funkcji lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>Polecany rozdział książki  
 [Obiekty delegowane, zdarzeń i wyrażenia Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) w [C# 3.0 Cookbook, trzecia edycja: ponad 250 rozwiązań dla programistów języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [LINQ (zapytania o języku zintegrowanym)](../../../csharp/programming-guide/concepts/linq/index.md)  
 [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [Drzewa wyrażeń](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Visual Studio 2008 C# przykłady (zobacz zapytań LINQ przykładowe pliki i XQuery program)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [Wyrażenia lambda cykliczne](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)

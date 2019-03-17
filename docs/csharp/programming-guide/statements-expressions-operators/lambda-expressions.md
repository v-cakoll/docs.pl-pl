---
title: Wyrażenia lambda - C# Programming Guide
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: dd9b77a90030a96d17104c8c0e48964b6a85d165
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125736"
---
# <a name="lambda-expressions-c-programming-guide"></a>Wyrażenia lambda (C# Programming Guide)

A *wyrażenia lambda* to blok kodu (wyrażenia lub blok instrukcji), który jest traktowany jako obiekt. Może być przekazywany jako argument do metody, a także mogą być zwrócone przez funkcję wywołania metody. Wyrażenia lambda są często używane do:

- Przekazywanie kodu, który jest wykonywany do metod asynchronicznych, takich jak <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.

- Zapisywanie [wyrażenia zapytań LINQ](../../linq/index.md).

- Tworzenie [drzew wyrażeń](../concepts/expression-trees/index.md).

Wyrażenia lambda są kod, który może być reprezentowany jako obiekt delegowany lub jako drzewo wyrażenia, który kompiluje do delegata. Typ delegata określonego wyrażenia lambda jest zależna od jego parametrów i zwracają wartość. Wyrażenia lambda, które nie zwracają wartości odpowiadają określonym `Action` delegować, w zależności od jego liczba parametrów. Wyrażenia lambda, które zwracają wartości odpowiadają określonym `Func` delegować, w zależności od jego liczba parametrów. Na przykład, wyrażenie lambda, która ma dwa parametry, ale nie zwraca żadnej wartości odnosi się do <xref:System.Action%602> delegować. Wyrażenie lambda, która ma jeden parametr i zwraca wartość odpowiada <xref:System.Func%602> delegować.

Używa wyrażenia lambda `=>`, [operatora deklaracji lambda](../../language-reference/operators/lambda-operator.md), aby oddzielić listą parametrów lambda z jego kodu wykonywalnego. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i umieścić blok wyrażenia lub instrukcji po drugiej stronie. Na przykład, wyrażenie lambda jednowierszowego `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów. To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Można także przypisać wyrażenia lambda do Typ drzewa wyrażeń:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Lub można je przekazać bezpośrednio jako argumentu metody:

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Kiedy używasz składni oparte na metodzie do wywołania <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in Class metoda <xref:System.Linq.Enumerable?displayProperty=nameWithType> klasy (tak jak w technologii LINQ do obiektów i LINQ to XML) parametr jest typem delegowanym <xref:System.Func%602?displayProperty=nameWithType>. Użycie wyrażenia lambda jest najwygodniejszym sposobem tworzenia delegata. Gdy wywołujesz <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in Class metoda <xref:System.Linq.Queryable?displayProperty=nameWithType> klasy (tak jak w składniku LINQ to SQL) typ parametru jest typ drzewa wyrażeń [ `Expression<Func<TSource,TResult>>` ](<xref:System.Linq.Expressions.Expression%601>). I znowu wyrażenie lambda jest tylko bardzo zwięzłym sposobem konstruowania takiego drzewa wyrażeń. Dzięki wyrażeniom lambda `Select` wywołania wyglądają podobnie, choć w rzeczywistości typ obiektu utworzonego z lambdy jest inny.

Wszystkie ograniczenia, które są stosowane do [anonimowymi](anonymous-methods.md) dotyczą także wyrażeń lambda.
  
## <a name="expression-lambdas"></a>Lambdy wyrażeń

Wyrażenie lambda z wyrażeniem po prawej stronie `=>` operator jest nazywany *wyrażenia lambda*. Lambdy wyrażeń są często używane w konstrukcji [drzew wyrażeń](../concepts/expression-trees/index.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

```csharp
(input-parameters) => expression
```

Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.

Określanie braku parametrów wejściowych za pomocą pustych nawiasów:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Czasami niemożliwe jest dla kompilatora wywnioskowanie typów wejściowych. Można określić typy jawne, jak pokazano w poniższym przykładzie:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Typy parametru wejściowego muszą być wszystkie jawne lub niejawne; w przeciwnym razie [CS0748](../../misc/cs0748.md) występuje błąd kompilatora.

Treść wyrażenia lambda może zawierać wywołania metody. Jednak w przypadku tworzenia drzew wyrażeń, które są obliczane poza kontekstem .NET środowiska uruchomieniowego języka wspólnego, takie jak w programie SQL Server, możesz nie należy używać metody wywołań w wyrażeniach lambda. Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.

## <a name="statement-lambdas"></a>Lambdy instrukcji

Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:

```csharp  
(input-parameters) => { statement; }
```

Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.
  
## <a name="async-lambdas"></a>Lambdy asynchroniczne

Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają Przetwarzanie asynchroniczne przy użyciu [async](../../language-reference/keywords/async.md) i [await](../../language-reference/keywords/await.md) słów kluczowych. Na przykład, poniższy przykład Windows Forms zawiera program obsługi zdarzeń, który wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync`.

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej. Aby dodać ten program obsługi `async` modyfikator przed listą parametrów lambda, co ilustruje poniższy przykład:

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Aby uzyskać więcej informacji na temat sposobu tworzenia i używania metod asynchronicznych, zobacz [Asynchronous Programming with async i await](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Wyrażenia lambda i krotki

Począwszy od C# 7.0, C# język zapewnia wbudowaną obsługę [krotek](../../tuples.md). Spójna Kolekcja może zapewnić jako argument do wyrażenia lambda i Wyrażenie lambda może również zwracać krotki. W niektórych przypadkach kompilator języka C# używa wnioskowanie o typie, aby określić typy elementów krotki.

Należy zdefiniować krotki umieszczając rozdzielana przecinkami lista składników w nawiasach. W poniższym przykładzie użyto krotki z trzech składników do przekazania w sekwencji liczb do wyrażenia lambda, rozwiązanie quorum zwiększa dwukrotnie każdej wartości, która zwraca krotki z trzech składników, który zawiera wynik mnożenia.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Zazwyczaj są nazywane polami krotki `Item1`, `Item2`itp. Można jednak zdefiniować krotki ze składnikami nazwane, tak jak w poniższym przykładzie.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Aby uzyskać więcej informacji na temat C# krotek, zobacz [ C# typy krotki](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdy ze standardowych operatorów zapytań

LINQ do obiektów, między innymi implementacjami posiada parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodziny ogólnych delegatów. Ci delegaci używać parametrów typu, aby zdefiniować liczbę i typ parametrów danych wejściowych oraz zwracany typ delegata. `Func` Obiekty delegowane są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Na przykład, rozważmy <xref:System.Func%602> typ delegata:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegat może być utworzone jako `Func<int, bool>` wystąpienia gdzie `int` jest parametrem wejściowym i `bool` jest wartością zwracaną. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Na przykład `Func<int, string, bool>` definiuje delegata z dwoma parametrami wejściowymi `int` i `string`, a zwracany typ `bool`. Następujące `Func` delegata, gdy jest wywoływana, zwraca wartość Boolean wskazującą, czy parametr wejściowy jest równy 5:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Można również dostarczyć Wyrażenie lambda, gdy typ argumentu jest <xref:System.Linq.Expressions.Expression%601>, na przykład w standardowych operatorów zapytań, które są zdefiniowane w <xref:System.Linq.Queryable> typu. Po określeniu <xref:System.Linq.Expressions.Expression%601> argument, wyrażenie lambda jest kompilowana do drzewa wyrażenie.
  
W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> standardowego operatora zapytania:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To konkretne wyrażenie lambda liczy te liczby całkowite (`n`) które podzielone przez dwa dają resztę 1.

Poniższy przykład tworzy sekwencję zawierającą wszystkie elementy w `numbers` tablica, która poprzedzać 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

W poniższym przykładzie określono wiele parametrów danych wejściowych, umieszczając je w nawiasach. Metoda ta zwraca wszystkie elementy w `numbers` tablicy, dopóki nie napotka liczby, w których wartość jest mniejsza niż jej porządkowym w tablicy:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda

Podczas pisania wyrażeń lambda, często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ bazując na treść lambda, typy parametrów i inne czynniki, zgodnie z opisem w C# specyfikacji języka. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Jeśli jest wykonywane zapytanie `IEnumerable<Customer>`, a następnie wywnioskowana jest zmienna wejściowa jest `Customer` obiektu, co oznacza, że masz dostęp do metod i właściwości:  

```csharp
customers.Where(c => c.City == "London");
```

Ogólne zasady wnioskowanie o typie dla wyrażeń lambda są następujące:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.
  
Należy pamiętać, że wyrażenia lambda same w sobie nie mają typu, ponieważ wspólny system typów nie używa wewnętrznej koncepcji "wyrażenia lambda". Jednak czasami wygodnie jest mówić potocznie o "type" wyrażenia lambda. W takich przypadkach typ odnosi się do typu delegata lub <xref:System.Linq.Expressions.Expression> typ do którego jest konwertowane Wyrażenie lambda.

## <a name="variable-scope-in-lambda-expressions"></a>Zakres zmiennych w wyrażeniach lambda

Wyrażenia lambda mogą odwoływać się do *zmiennych zewnętrznych* (zobacz [anonimowymi](anonymous-methods.md)) znajdujących się w zasięgu w metodzie, która definiuje wyrażenie lambda lub w zakresie typu, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano te reguły:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:  

- Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.

- Zmienne zawarte w wyrażeniu lambda nie są widoczne w otaczającej go metodzie.

- Wyrażenie lambda nie może bezpośrednio przechwycić [w](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), lub [się](../../language-reference/keywords/out-parameter-modifier.md) parametr z otaczającym metody.

- A [zwracają](../../language-reference/keywords/return.md) instrukcji w wyrażeniu lambda nie powoduje otaczającej go metodzie do zwrócenia.

- Wyrażenie lambda nie może zawierać [goto](../../language-reference/keywords/goto.md), [podziału](../../language-reference/keywords/break.md), lub [nadal](../../language-reference/keywords/continue.md) instrukcji, jeśli obiekt docelowy, szybkie instrukcji znajduje się poza blokiem wyrażenia lambda. Jest również błędu, aby mieć instrukcja skoku poza blok wyrażenia lambda, jeśli element docelowy znajduje się wewnątrz bloku.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyrażenia funkcji anonimowych](~/_csharplang/spec/expressions.md#anonymous-function-expressions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>polecany rozdział książki

[Delegatów, zdarzeń i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3.0 Cookbook, Third Edition: Ponad 250 rozwiązań dla C# ekspertów w programowaniu w wersji 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [LINQ (Language-Integrated Query)](../concepts/linq/index.md)
- [Metody anonimowe](anonymous-methods.md)
- [Drzewa wyrażeń](../concepts/expression-trees/index.md)
- [Funkcje lokalne w porównaniu do wyrażenia lambda](../../local-functions-vs-lambdas.md)
- [Wyrażenia lambda niejawnie wpisane](../../implicitly-typed-lambda-expressions.md)
- [Visual Studio 2008 C# Samples (zobacz pliki LINQ przykładowe zapytania i XQuery program)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Powtarzalne wyrażenia lambda](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)

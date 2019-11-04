---
title: Wyrażenia lambda — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: d401c832dd3b29de609e9eaab69ea3334d6591b9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417684"
---
# <a name="lambda-expressions-c-programming-guide"></a>Wyrażenia lambda (C# Przewodnik programowania)

*Wyrażenie lambda* jest wyrażeniem jednej z następujących dwóch form:

- [Wyrażenie lambda](#expression-lambdas) , które ma wyrażenie jako treść:

  ```csharp
  (input-parameters) => expression
  ```

- [Instrukcja lambda](#statement-lambdas) , która ma blok instrukcji jako treść:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Użyj [operatora deklaracji lambda `=>`](../../language-reference/operators/lambda-operator.md) , aby oddzielić listę parametrów lambda z jej treści. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i wyrażenie lub blok instrukcji po drugiej stronie.

Każde wyrażenie lambda można przekonwertować na typ [delegata](../../language-reference/builtin-types/reference-types.md#the-delegate-type) . Typ delegata, do którego można przekonwertować wyrażenie lambda, jest definiowany przez typy jego parametrów i wartość zwracaną. Jeśli wyrażenie lambda nie zwraca wartości, można je przekonwertować na jeden z typów delegatów `Action`; w przeciwnym razie można ją przekonwertować na jeden z typów delegatów `Func`. Na przykład wyrażenie lambda, które ma dwa parametry i nie zwraca żadnej wartości, można przekonwertować na delegata <xref:System.Action%602>. Wyrażenie lambda, które ma jeden parametr i zwraca wartość, można przekonwertować na delegata <xref:System.Func%602>. W poniższym przykładzie wyrażenie lambda `x => x * x`, które określa parametr o nazwie `x` i zwraca wartość `x` kwadratowego, jest przypisywana do zmiennej typu delegata:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Wyrażenia lambda można również przekonwertować na typy [drzewa wyrażeń](../concepts/expression-trees/index.md) , jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Można użyć wyrażeń lambda w dowolnym kodzie, który wymaga wystąpienia typów delegatów lub drzew wyrażeń, na przykład jako argumentu metody <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>, aby przekazać kod, który powinien zostać wykonany w tle. Można również użyć wyrażeń lambda podczas pisania [LINQ in C# ](../../linq/index.md), jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Przy użyciu składni opartej na metodzie wywoływanie metody <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> w klasie <xref:System.Linq.Enumerable?displayProperty=nameWithType>, na przykład w LINQ to Objects i LINQ to XML, parametr jest typem delegata <xref:System.Func%602?displayProperty=nameWithType>. W przypadku wywołania metody <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> w klasie <xref:System.Linq.Queryable?displayProperty=nameWithType>, na przykład w LINQ to SQL, typem parametru jest [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)typ drzewa wyrażenia. W obu przypadkach można użyć tego samego wyrażenia lambda, aby określić wartość parametru. Dzięki temu dwa `Select` wywołania wyglądają podobnie, chociaż w rzeczywistości typ obiektów utworzonych na podstawie wyrażeń lambda jest różny.
  
## <a name="expression-lambdas"></a>Wyrażenia lambda

Wyrażenie lambda z wyrażeniem po prawej stronie operatora `=>` jest nazywane *wyrażeniem lambda*. Wyrażenia lambda są szeroko używane w konstruowaniu [drzew wyrażeń](../concepts/expression-trees/index.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

```csharp
(input-parameters) => expression
```

Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.

Określanie braku parametrów wejściowych za pomocą pustych nawiasów:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Czasami w kompilatorze nie można wywnioskować typów wejściowych. Możesz określić typy jawnie, jak pokazano w następującym przykładzie:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Typy parametrów wejściowych muszą być jawne lub niejawne; w przeciwnym razie wystąpi błąd kompilatora [CS0748](../../misc/cs0748.md) .

Treść wyrażenia lambda może składać się z wywołania metody. Jeśli jednak tworzysz drzewa wyrażeń, które są oceniane poza kontekstem środowiska uruchomieniowego języka wspólnego .NET, na przykład w SQL Server, nie należy używać wywołań metod w wyrażeniach lambda. Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.

## <a name="statement-lambdas"></a>Instrukcja lambda

Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Instrukcji lambda nie można używać do tworzenia drzew wyrażeń.
  
## <a name="async-lambdas"></a>Asynchroniczne wyrażenia lambda

Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają asynchroniczne przetwarzanie przy użyciu słów kluczowych [Async](../../language-reference/keywords/async.md) i [await](../../language-reference/operators/await.md) . Na przykład poniższy Windows Forms przykład zawiera procedurę obsługi zdarzeń, która wywołuje i czeka na metodę asynchroniczną, `ExampleMethodAsync`.

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

Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej. Aby dodać tę procedurę obsługi, Dodaj modyfikator `async` przed listą parametrów lambda, jak pokazano na poniższym przykładzie:

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

Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i await](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Wyrażenia lambda i krotki

Począwszy od C# 7,0, C# język zapewnia wbudowaną obsługę [krotek](../../tuples.md). Można podać krotkę jako argument wyrażenia lambda, a wyrażenie lambda może również zwracać krotkę. W niektórych przypadkach C# kompilator używa wnioskowania o typie, aby określić typy składników spójnych kolekcji.

Można zdefiniować krotkę, umieszczając w nawiasach rozdzielaną przecinkami listę składników. Poniższy przykład używa krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca spójną kolekcję z trzema składnikami, które zawierają wynik mnożenia.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Zwykle pola krotki mają nazwę `Item1`, `Item2`itd. Można jednak zdefiniować krotkę z nazwanymi składnikami, tak jak w poniższym przykładzie.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Aby uzyskać więcej informacji C# na temat krotek, zobacz [ C# typy krotek](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Wyrażenia lambda ze standardowymi operatorami zapytań

LINQ to Objects, między innymi implementacjami, mają parametr wejściowy, którego typ jest jedną z <xref:System.Func%601> rodziny delegatów ogólnych. Te Delegaty używają parametrów typu, aby zdefiniować liczbę i typ parametrów wejściowych oraz zwracany typ delegata. Delegaty `Func` są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Rozważmy na przykład typ delegata <xref:System.Func%602>:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegat można utworzyć jako wystąpienie `Func<int, bool>`, gdzie `int` jest parametrem wejściowym, a `bool` jest wartością zwracaną. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Na przykład `Func<int, string, bool>` definiuje delegata z dwoma parametrami wejściowymi, `int` i `string`oraz typem zwracanym `bool`. Następujący `Func` delegat, gdy jest wywoływany, zwraca wartość logiczną wskazującą, czy parametr wejściowy jest równy pięć:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Możesz również podać wyrażenie lambda, gdy typem argumentu jest <xref:System.Linq.Expressions.Expression%601>, na przykład w standardowych operatory zapytań, które są zdefiniowane w typie <xref:System.Linq.Queryable>. Po określeniu argumentu <xref:System.Linq.Expressions.Expression%601> lambda jest kompilowane do drzewa wyrażenia.
  
W poniższym przykładzie użyto standardowego operatora zapytania <xref:System.Linq.Enumerable.Count%2A>:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To konkretne wyrażenie lambda liczy te liczby całkowite (`n`), które po poddzieleniu przez dwa mają pozostałą część 1.

Poniższy przykład tworzy sekwencję zawierającą wszystkie elementy w tablicy `numbers`, która poprzedza 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

W poniższym przykładzie określono wiele parametrów wejściowych, umieszczając je w nawiasach. Metoda zwraca wszystkie elementy w tablicy `numbers`, dopóki nie napotka liczby, której wartość jest mniejsza niż jej pozycja porządkowa w tablicy:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda

Podczas pisania wyrażeń lambda często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ na podstawie treści wyrażenia lambda, typów parametrów i innych czynników, zgodnie z opisem w specyfikacji C# języka. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Jeśli wykonujesz zapytanie do `IEnumerable<Customer>`, zmienna wejściowa jest wywnioskowana jako obiekt `Customer`, co oznacza, że masz dostęp do jego metod i właściwości:  

```csharp
customers.Where(c => c.City == "London");
```

Ogólne reguły wnioskowania o typie dla wyrażeń lambda są następujące:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.
  
Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie ma wewnętrznej koncepcji "wyrażenie lambda". Jednak czasami wygodnie jest mówić nieformalnie "Type" wyrażenia lambda. W takich przypadkach typ odnosi się do typu delegata lub typu <xref:System.Linq.Expressions.Expression>, do którego jest konwertowane wyrażenie lambda.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Przechwycenie zmiennych zewnętrznych i zakresu zmiennych w wyrażeniach lambda

Wyrażenia lambda mogą odwoływać się do *zmiennych zewnętrznych*. Są to zmienne, które znajdują się w zakresie metody, która definiuje wyrażenie lambda lub w zakresie typu, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano te reguły:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:  

- Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.

- Zmienne wprowadzone w wyrażeniu lambda nie są widoczne w otaczającej metodzie.

- Wyrażenie lambda nie może bezpośrednio przechwycić parametru [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)lub [out](../../language-reference/keywords/out-parameter-modifier.md) z otaczającej metody.

- Instrukcja [Return](../../language-reference/keywords/return.md) w wyrażeniu lambda nie powoduje zwrócenia otaczającej metody.

- Wyrażenie lambda nie może zawierać instrukcji [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)ani [Continue](../../language-reference/keywords/continue.md) , jeśli element docelowy instrukcji skoku znajduje się poza blokiem wyrażenia lambda. Występuje również błąd instrukcji skoku poza blokiem wyrażenia lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>polecany rozdział książki

[Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3,0 Cookbook, wydanie trzecie: więcej niż 250 rozwiązań dla C# 3,0 programistów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [LINQ (zapytanie zintegrowane z językiem)](../concepts/linq/index.md)
- [Drzewa wyrażeń](../concepts/expression-trees/index.md)
- [Funkcje lokalne w porównaniu z wyrażeniami lambda](../../local-functions-vs-lambdas.md)
- [Niejawnie wpisane wyrażenia lambda](../../implicitly-typed-lambda-expressions.md)
- [Przykłady dla programu C# Visual Studio 2008 (Zobacz pliki przykładowe zapytania LINQ i program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Cykliczne wyrażenia lambda](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)

---
title: Wyrażenia Lambda - Przewodnik programowania C#
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: c549b9fcc91401aed846afd39e656b60e16afb74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937601"
---
# <a name="lambda-expressions-c-programming-guide"></a>Wyrażenia Lambda (Przewodnik programowania C#)

Wyrażenie *lambda* jest wyrazem dowolnej z następujących dwóch form:

- [Wyrażenie lambda,](#expression-lambdas) które ma wyrażenie jako jego treść:

  ```csharp
  (input-parameters) => expression
  ```

- [Oświadczenie lambda,](#statement-lambdas) który ma blok instrukcji jako jego ciało:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Użyj [operatora `=>` deklaracji lambda,](../../language-reference/operators/lambda-operator.md) aby oddzielić listę parametrów lambdy od jego treści. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i wyrażenie lub blok instrukcji po drugiej stronie.

Każde wyrażenie lambda można przekonwertować na typ [delegata.](../../language-reference/builtin-types/reference-types.md#the-delegate-type) Typ delegata, na który można przekonwertować wyrażenie lambda, jest definiowany przez typy jego parametrów i wartość zwracaną. Jeśli wyrażenie lambda nie zwraca wartości, można go przekonwertować `Action` na jeden z typów delegatów; w przeciwnym razie można go przekonwertować na jeden z typów delegatów. `Func` Na przykład wyrażenie lambda, które ma dwa parametry i zwraca <xref:System.Action%602> wartość nie można przekonwertować na delegata. Wyrażenie lambda, który ma jeden parametr i zwraca <xref:System.Func%602> wartość można przekonwertować na delegata. W poniższym przykładzie wyrażenie `x => x * x`lambda , które określa parametr, który jest nazwany `x` i zwraca wartość kwadratu, `x` jest przypisany do zmiennej typu delegata:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Wyrażenie lambdas również można przekonwertować na typy [drzewa wyrażeń,](../concepts/expression-trees/index.md) jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Wyrażenia lambda można użyć w dowolnym kodzie, który wymaga wystąpień typów delegatów <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> lub drzew wyrażeń, na przykład jako argument do metody, aby przekazać kod, który powinien być wykonywany w tle. Można również użyć wyrażeń lambda podczas pisania [LINQ w języku C#,](../../linq/index.md)jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

W przypadku użycia składni opartej <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> na metodach do wywołania metody w <xref:System.Linq.Enumerable?displayProperty=nameWithType> klasie, na przykład w LINQ <xref:System.Func%602?displayProperty=nameWithType>do obiektów i LINQ do XML, parametr jest typem delegata . Podczas wywoływania <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> w klasie, na przykład w LINQ do SQL, [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)typ parametru jest typem drzewa wyrażeń . W obu przypadkach można użyć tego samego wyrażenia lambda, aby określić wartość parametru. To sprawia, `Select` że dwa wywołania wyglądać podobnie, chociaż w rzeczywistości typ obiektów utworzonych z lambdas jest inny.
  
## <a name="expression-lambdas"></a>Wyrażenie lambdas

Wyrażenie lambda z wyrażeniem po prawej `=>` stronie operatora jest nazywany *wyrażenie lambda*. Wyrażenie lambdas są szeroko stosowane w budowie [drzew ekspresji](../concepts/expression-trees/index.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

```csharp
(input-parameters) => expression
```

Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.

Określanie braku parametrów wejściowych za pomocą pustych nawiasów:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Czasami jest niemożliwe dla kompilatora wywnioskować typy danych wejściowych. Można określić typy jawnie, jak pokazano w poniższym przykładzie:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Typy parametrów wejściowych muszą być wszystkie jawne lub wszystkie niejawne; w przeciwnym razie wystąpi błąd kompilatora [CS0748.](../../misc/cs0748.md)

Treść wyrażenia lambda może składać się z wywołania metody. Jednak jeśli tworzysz drzewa wyrażeń, które są oceniane poza kontekstem .NET common language runtime, takich jak w programie SQL Server, nie należy używać wywołań metody w wyrażeniach lambda. Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.

## <a name="statement-lambdas"></a>Oświadczenie lambdas

Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Instrukcja lambdas nie można użyć do tworzenia drzew wyrażeń.
  
## <a name="async-lambdas"></a>Async lambdas

Można łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają przetwarzanie asynchroniczne przy użyciu [asynchronicznych](../../language-reference/keywords/async.md) i [await](../../language-reference/operators/await.md) słów kluczowych. Na przykład poniższy przykład formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje i oczekuje na metodę asynchronia . `ExampleMethodAsync`

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

Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej. Aby dodać ten program `async` obsługi, dodaj modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie:

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

Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [Programowanie asynchroniczne z asynchroniczną asynchroniczną i oczekując](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Wyrażenia lambda i krotek

Począwszy od języka C# 7.0, język Języka C# zapewnia wbudowaną obsługę [krotek](../../tuples.md). Można podać krotki jako argument do wyrażenia lambda i wyrażenie lambda można również zwrócić krotki. W niektórych przypadkach kompilator C# używa wnioskowania o typie do określenia typów składników krotki.

Krotkę można zdefiniować, załączając listę jej składników rozdzielaną przecinkami w nawiasach. W poniższym przykładzie użyto krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca krotkę z trzema składnikami, która zawiera wynik mnożenia.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Zwykle pola krotki są nazwane `Item1`, `Item2`itp. Można jednak zdefiniować krotkę z nazwanymi składnikami, tak jak w poniższym przykładzie.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Aby uzyskać więcej informacji na temat krotek języka C#, zobacz [Typy krotki języka C#.](../../tuples.md)

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas ze standardowymi operatorami zapytań

LINQ do obiektów, wśród innych implementacji mają parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodziny delegatów ogólnych. Te delegatów użyć parametrów typu do definiowania liczby i typu parametrów wejściowych i zwracany typ delegata. `Func`delegatów są bardzo przydatne do hermetyzacji wyrażenia zdefiniowane przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Rozważmy na <xref:System.Func%602> przykład typ delegata:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegata można utworzyć wystąpienie jako `Func<int, bool>` wystąpienie, `int` w którym `bool` jest parametrem wejściowym i jest wartością zwracaną. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Na przykład `Func<int, string, bool>` definiuje delegata z dwoma parametrami wejściowymi `int` i `string` `bool`, i typu zwracanego . Następujący `Func` delegat, gdy jest wywoływany, zwraca wartość logiczną, która wskazuje, czy parametr wejściowy jest równa pięciu:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Można również podać wyrażenie lambda, gdy <xref:System.Linq.Expressions.Expression%601>typ argumentu jest , na przykład w <xref:System.Linq.Queryable> standardowych operatorów kwerend, które są zdefiniowane w typie. Po określeniu <xref:System.Linq.Expressions.Expression%601> argumentu lambda jest kompilowany do drzewa wyrażeń.
  
W poniższym <xref:System.Linq.Enumerable.Count%2A> przykładzie użyto standardowego operatora kwerendy:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To szczególne wyrażenie lambda zlicza`n`te liczby całkowite ( ), które po podziale przez dwa mają pozostałą część 1.

Poniższy przykład tworzy sekwencję, która zawiera `numbers` wszystkie elementy w tablicy, które poprzedzają 9, ponieważ jest to pierwsza liczba w sekwencji, która nie spełnia warunku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

W poniższym przykładzie określono wiele parametrów wejściowych, załączając je w nawiasy. Metoda zwraca wszystkie elementy `numbers` w tablicy, dopóki nie napotka liczby, której wartość jest mniejsza niż jego pozycja porządna w tablicy:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda

Podczas pisania lambdas, często nie trzeba określić typ dla parametrów wejściowych, ponieważ kompilator można wywnioskować typ na podstawie obiektu lambda, typy parametrów i inne czynniki opisane w specyfikacji języka C#. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Jeśli jesteś wykonywania `IEnumerable<Customer>`kwerendy , a następnie zmienna `Customer` wejściowa jest wywnioskować jako obiekt, co oznacza, że masz dostęp do jego metod i właściwości:  

```csharp
customers.Where(c => c.City == "London");
```

Ogólne zasady wnioskowania o typie lambdas są następujące:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.
  
Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ wspólny system typów nie ma wewnętrznej koncepcji "wyrażenia lambda". Jednak czasami wygodnie jest mówić nieformalnie o "typie" wyrażenia lambda. W takich przypadkach typ odnosi się do <xref:System.Linq.Expressions.Expression> typu lub typu delegata, na które konwertowano wyrażenie lambda.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Przechwytywanie zmiennych zewnętrznych i zakresu zmiennych w wyrażeniach lambda

Lambdas może odwoływać się do *zmiennych zewnętrznych*. Są to zmienne, które znajdują się w zakresie w metodzie, która definiuje wyrażenie lambda lub w zakresie w typie, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano te reguły:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:  

- Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.

- Zmienne wprowadzone w wyrażeniu lambda nie są widoczne w otaczającej metody.

- Wyrażenie lambda nie może bezpośrednio przechwytywać [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)lub [out](../../language-reference/keywords/out-parameter-modifier.md) parametr u otaczania metody.

- Return [return](../../language-reference/keywords/return.md) instrukcji w wyrażeniu lambda nie powoduje otaczającej metody do zwrócenia.

- Wyrażenie lambda nie może zawierać [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), lub [continue](../../language-reference/keywords/continue.md) instrukcji, jeśli obiekt docelowy tej instrukcji skoku znajduje się poza blokiem wyrażenia lambda. Jest to również błąd, aby mieć instrukcję skoku poza blokiem wyrażenia lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="featured-book-chapter"></a>Polecany rozdział książki

[Delegaci, zdarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów Języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [LINQ (zapytanie zintegrowane z językiem)](../concepts/linq/index.md)
- [Drzewa wyrażeń](../concepts/expression-trees/index.md)
- [Funkcje lokalne w porównaniu z wyrażeniami lambda](../../local-functions-vs-lambdas.md)
- [Wyrażenia lambda wpisane niejawnie](../../implicitly-typed-lambda-expressions.md)
- [Przykłady języka C# programu Visual Studio 2008 (zobacz pliki przykładowych zapytań LINQ i program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Cykliczne wyrażenia lambda](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)

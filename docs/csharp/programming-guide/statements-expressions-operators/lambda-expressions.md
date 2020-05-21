---
title: Wyrażenia lambda — Przewodnik programowania w języku C#
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: b86fe4fd91b395498926512650490f8d3a0383a1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761840"
---
# <a name="lambda-expressions-c-programming-guide"></a>Wyrażenia lambda (Przewodnik programowania w języku C#)

*Wyrażenie lambda* jest wyrażeniem jednej z następujących dwóch form:

- [Wyrażenie lambda](#expression-lambdas) , które ma wyrażenie jako treść:

  ```csharp
  (input-parameters) => expression
  ```

- [Instrukcja lambda](#statement-lambdas) , która ma blok instrukcji jako treść:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Użyj [ `=>` operatora deklaracji lambda](../../language-reference/operators/lambda-operator.md) , aby oddzielić listę parametrów lambda z jej treści. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i wyrażenie lub blok instrukcji po drugiej stronie.

Każde wyrażenie lambda można przekonwertować na typ [delegata](../../language-reference/builtin-types/reference-types.md#the-delegate-type) . Typ delegata, do którego można przekonwertować wyrażenie lambda, jest definiowany przez typy jego parametrów i wartość zwracaną. Jeśli wyrażenie lambda nie zwraca wartości, można je przekonwertować na jeden z `Action` typów delegatów; w przeciwnym razie można je przekonwertować na jeden z `Func` typów delegatów. Na przykład wyrażenie lambda, które ma dwa parametry i nie zwraca żadnej wartości, można przekonwertować na <xref:System.Action%602> delegata. Wyrażenie lambda, które ma jeden parametr i zwraca wartość, można przekonwertować na <xref:System.Func%602> obiekt delegowany. W poniższym przykładzie wyrażenie lambda `x => x * x` , które określa parametr o nazwie `x` i zwraca wartość `x` kwadratową, jest przypisywana do zmiennej typu delegata:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Wyrażenia lambda można również przekonwertować na typy [drzewa wyrażeń](../concepts/expression-trees/index.md) , jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Można użyć wyrażeń lambda w dowolnym kodzie, który wymaga wystąpienia typów delegatów lub drzew wyrażeń, na przykład jako argumentu <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> metody, aby przekazać kod, który powinien być wykonany w tle. Można również użyć wyrażeń lambda podczas pisania [LINQ w języku C#](../../linq/index.md), jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

W przypadku użycia składni opartej na metodzie do wywołania <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> metody w <xref:System.Linq.Enumerable?displayProperty=nameWithType> klasie, na przykład w LINQ to Objects i LINQ to XML, parametr jest typem delegata <xref:System.Func%602?displayProperty=nameWithType> . Po wywołaniu <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody w <xref:System.Linq.Queryable?displayProperty=nameWithType> klasie, na przykład w LINQ to SQL, typem parametru jest typ drzewa wyrażenia [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) . W obu przypadkach można użyć tego samego wyrażenia lambda, aby określić wartość parametru. Powoduje to, że dwa `Select` wywołania wyglądają podobnie, chociaż w rzeczywistości typ obiektów utworzonych na podstawie wyrażeń lambda jest różny.
  
## <a name="expression-lambdas"></a>Wyrażenia lambda

Wyrażenie lambda z wyrażeniem po prawej stronie `=>` operatora jest nazywane *wyrażeniem lambda*. Wyrażenia lambda są szeroko używane w konstruowaniu [drzew wyrażeń](../concepts/expression-trees/index.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

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

Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają asynchroniczne przetwarzanie przy użyciu słów kluczowych [Async](../../language-reference/keywords/async.md) i [await](../../language-reference/operators/await.md) . Na przykład poniższy Windows Forms przykład zawiera procedurę obsługi zdarzeń, która wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync` .

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

Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej. Aby dodać ten program obsługi, Dodaj `async` modyfikator przed listą parametrów lambda, jak pokazano na poniższym przykładzie:

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

Począwszy od języka C# 7,0, język C# zapewnia wbudowaną obsługę [krotek](../../tuples.md). Można podać krotkę jako argument wyrażenia lambda, a wyrażenie lambda może również zwracać krotkę. W niektórych przypadkach kompilator języka C# używa wnioskowania o typie, aby określić typy składników spójnych kolekcji.

Można zdefiniować krotkę, umieszczając w nawiasach rozdzielaną przecinkami listę składników. Poniższy przykład używa krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca spójną kolekcję z trzema składnikami, które zawierają wynik mnożenia.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Zwykle pola krotki mają nazwę `Item1` , `Item2` itp. Można jednak zdefiniować krotkę z nazwanymi składnikami, tak jak w poniższym przykładzie.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Aby uzyskać więcej informacji na temat krotek języka C#, zobacz [typy krotek języka c#](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Wyrażenia lambda ze standardowymi operatorami zapytań

LINQ to Objects, między innymi implementacjami, mają parametr wejściowy, którego typ jest jedną z <xref:System.Func%601> rodziny delegatów ogólnych. Te Delegaty używają parametrów typu, aby zdefiniować liczbę i typ parametrów wejściowych oraz zwracany typ delegata. `Func`Delegaty są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Rozważmy na przykład <xref:System.Func%602> typ delegata:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegat można utworzyć jako `Func<int, bool>` wystąpienie, gdzie `int` jest parametrem wejściowym i `bool` jest wartością zwracaną. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Na przykład `Func<int, string, bool>` definiuje delegata z dwoma parametrami wejściowymi `int` i `string` i typem zwracanym `bool` . Następujący `Func` Delegat, gdy jest wywoływany, zwraca wartość logiczną, która wskazuje, czy parametr wejściowy jest równy pięć:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Można również podać wyrażenie lambda, gdy typem argumentu jest <xref:System.Linq.Expressions.Expression%601> , na przykład w standardowych operatorów zapytań, które są zdefiniowane w <xref:System.Linq.Queryable> typie. Po określeniu <xref:System.Linq.Expressions.Expression%601> argumentu lambda jest kompilowane do drzewa wyrażenia.
  
W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> standardowego operatora zapytania:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To konkretne wyrażenie lambda liczy te liczby całkowite ( `n` ), które podzielone przez dwa mają resztę 1.

Poniższy przykład tworzy sekwencję zawierającą wszystkie elementy w `numbers` tablicy, która poprzedza 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

W poniższym przykładzie określono wiele parametrów wejściowych, umieszczając je w nawiasach. Metoda zwraca wszystkie elementy w `numbers` tablicy do momentu napotkania liczby, której wartość jest mniejsza niż jej pozycja porządkowa w tablicy:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda

Podczas pisania wyrażeń lambda często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ na podstawie treści wyrażenia lambda, typów parametrów i innych czynników, zgodnie z opisem w specyfikacji języka C#. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Jeśli wykonujesz zapytania `IEnumerable<Customer>` , wówczas zmienna wejściowa jest wywnioskowana jako `Customer` obiekt, co oznacza, że masz dostęp do jego metod i właściwości:  

```csharp
customers.Where(c => c.City == "London");
```

Ogólne reguły wnioskowania o typie dla wyrażeń lambda są następujące:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.
  
Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie ma wewnętrznej koncepcji "wyrażenie lambda". Jednak czasami wygodnie jest mówić nieformalnie "Type" wyrażenia lambda. W takich przypadkach typ odwołuje się do typu delegata lub <xref:System.Linq.Expressions.Expression> typu, do którego wyrażenie lambda jest konwertowane.

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

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>Polecany rozdział książki

[Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [języku c# 3,0 Cookbook, wydanie trzecie: więcej niż 250 rozwiązań dla programistów 3,0 c#](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [LINQ (zapytanie zintegrowane z językiem)](../concepts/linq/index.md)
- [Drzewa wyrażeń](../concepts/expression-trees/index.md)
- [Funkcje lokalne a wyrażenia lambda](../classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [Visual Studio 2008 — przykłady w języku C# (Zobacz pliki przykładowe zapytania LINQ i program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Cykliczne wyrażenia lambda](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)

---
title: Wyrażenia Lambda — Przewodnik programowania języka C#
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 6fd2dab09fe97aa4af87d82e2d23664c4347c8b3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101998"
---
# <a name="lambda-expressions-c-programming-guide"></a>Wyrażenia Lambda (Przewodnik programowania języka C#)

Wyrażenie *lambda* jest wyrażeniem dowolnej z następujących dwóch form:

- [Wyrażenie lambda,](#expression-lambdas) które ma wyrażenie jako jego ciało:

  ```csharp
  (input-parameters) => expression
  ```

- [Instrukcja lambda,](#statement-lambdas) która ma blok instrukcji jako jego treść:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Operator [deklaracji `=>` lambda](../../language-reference/operators/lambda-operator.md) służy do oddzielania listy parametrów lambda od jego treści. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i wyrażenie lub blok instrukcji po drugiej stronie.

Dowolne wyrażenie lambda można przekonwertować na typ [delegata.](../../language-reference/builtin-types/reference-types.md#the-delegate-type) Typ delegata, na który można przekonwertować wyrażenie lambda, jest definiowany przez typy jego parametrów i wartość zwracaną. Jeśli wyrażenie lambda nie zwraca wartości, można go przekonwertować na `Action` jeden z typów delegata; w przeciwnym razie można go przekonwertować na `Func` jeden z typów delegata. Na przykład wyrażenie lambda, który ma dwa parametry i zwraca <xref:System.Action%602> żadną wartość można przekonwertować na pełnomocnika. Wyrażenie lambda, który ma jeden parametr i zwraca <xref:System.Func%602> wartość można przekonwertować na pełnomocnika. W poniższym przykładzie wyrażenie `x => x * x`lambda , które określa `x` parametr, który `x` jest nazwany i zwraca wartość kwadratu, jest przypisany do zmiennej typu delegata:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Wyrażenie lambdas można również przekonwertować na typy [drzew wyrażeń,](../concepts/expression-trees/index.md) jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Można użyć wyrażeń lambda w dowolnym kodzie, który wymaga wystąpień typów <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> delegatów lub drzew wyrażeń, na przykład jako argument do metody przekazywania kodu, który powinien być wykonywany w tle. Można również użyć wyrażeń lambda podczas pisania [LINQ w języku C#](../../linq/index.md), jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

W przypadku używania składni opartej <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> na <xref:System.Linq.Enumerable?displayProperty=nameWithType> metodzie do wywoływania metody w klasie, na przykład w LINQ do obiektów i LINQ do XML, parametr jest typem <xref:System.Func%602?displayProperty=nameWithType>delegata . Po wywołaniu <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> w klasie, na przykład w LINQ do SQL, [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)typ parametru jest typem drzewa wyrażeń . W obu przypadkach można użyć tego samego wyrażenia lambda, aby określić wartość parametru. To sprawia, `Select` że dwa wywołania wyglądają podobnie, chociaż w rzeczywistości typ obiektów utworzonych z lambdas jest inny.
  
## <a name="expression-lambdas"></a>Wyrażenie lambdas

Wyrażenie lambda z wyrażeniem po prawej `=>` stronie operatora jest nazywane *wyrażeniem lambda*. Wyrażenie lambdas są szeroko stosowane w budowie [drzew ekspresji](../concepts/expression-trees/index.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

```csharp
(input-parameters) => expression
```

Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.

Określanie braku parametrów wejściowych za pomocą pustych nawiasów:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Czasami jest to niemożliwe dla kompilatora wywnioskować typy danych wejściowych. Można określić typy jawnie, jak pokazano w poniższym przykładzie:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Typy parametrów wejściowych muszą być jawne lub wszystkie niejawne; w przeciwnym razie wystąpi błąd kompilatora [CS0748.](../../misc/cs0748.md)

Treść wyrażenia lambda może składać się z wywołania metody. Jednak jeśli tworzysz drzewa wyrażeń, które są oceniane poza kontekstem środowiska wykonawczego języka wspólnego .NET, na przykład w programie SQL Server, nie należy używać wywołań metod w wyrażeniach lambda. Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.

## <a name="statement-lambdas"></a>Oświadczenie lambdas

Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Instrukcja lambdas nie może służyć do tworzenia drzew wyrażeń.
  
## <a name="async-lambdas"></a>Jagnięcina asynchronizów

Można łatwo utworzyć wyrażenia lambda i instrukcje, które zawierają przetwarzanie asynchroniczne przy użyciu [asynchronicznych](../../language-reference/keywords/async.md) i [await](../../language-reference/operators/await.md) słowa kluczowe. Na przykład poniższy przykład formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje metodę asynchronizową i oczekuje na metodę asynchronizowania. `ExampleMethodAsync`

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

Aby uzyskać więcej informacji na temat tworzenia i używania metod [asynchronicznych, zobacz Programowanie asynchroniczne za pomocą asynchronii i czekaj](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Wyrażenia lambda i krotek

Począwszy od języka C# 7.0, język C# zapewnia wbudowaną obsługę [krotek.](../../tuples.md) Można podać krotek jako argument do wyrażenia lambda i wyrażenie lambda może również zwrócić krotki. W niektórych przypadkach kompilator języka C# używa wnioskowania o typie do określenia typów składników krotki.

Krotka definiuje się, otaczając listę rozdzielanych przecinkami jej komponentów w nawiasach. W poniższym przykładzie użyto krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca krotki z trzema składnikami, która zawiera wynik mnożenia.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Zazwyczaj pola krotki są nazwane `Item1`, `Item2`itp. Można jednak zdefiniować krotek z nazwanych składników, jak w poniższym przykładzie nie.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Aby uzyskać więcej informacji na temat krotek języka C#, zobacz [typy krotek języka C#.](../../tuples.md)

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas ze standardowymi operatorami zapytań

LINQ do obiektów, wśród innych implementacji, mają parametr <xref:System.Func%601> wejściowy, którego typ jest jednym z rodziny delegatów rodzajowych. Te delegatów używać parametrów typu do definiowania liczby i typu parametrów wejściowych i typu zwracanego delegata. `Func`delegatów są bardzo przydatne do hermetyzacji wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Rozważmy na <xref:System.Func%602> przykład typ delegata:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Pełnomocnik może być wystąpienia jako `Func<int, bool>` wystąpienie, gdzie `int` `bool` jest parametrem wejściowym i jest wartością zwracaną. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Na przykład `Func<int, string, bool>` definiuje delegata z dwoma `int` `string`parametrami wejściowymi `bool`oraz i typem zwracanym . Następujący `Func` delegat, gdy jest wywoływany, zwraca wartość logiczną, która wskazuje, czy parametr wejściowy jest równy pięciu:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Można również podać wyrażenie lambda, gdy <xref:System.Linq.Expressions.Expression%601>typ argumentu jest , na przykład <xref:System.Linq.Queryable> w standardowych operatorów kwerend, które są zdefiniowane w typie. Po określeniu <xref:System.Linq.Expressions.Expression%601> argumentu lambda jest kompilowany do drzewa wyrażeń.
  
W poniższym przykładzie użyto standardowego <xref:System.Linq.Enumerable.Count%2A> operatora kwerendy:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To szczególne wyrażenie lambda zlicza`n`te liczby całkowite ( ), które po podzieleniu przez dwa mają pozostałą część 1.

Poniższy przykład tworzy sekwencję, która `numbers` zawiera wszystkie elementy w tablicy, które poprzedzają 9, ponieważ jest to pierwsza liczba w sekwencji, która nie spełnia warunku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Poniższy przykład określa wiele parametrów wejściowych, otaczając je w nawiasach. Metoda zwraca wszystkie elementy `numbers` w tablicy, dopóki nie napotka liczby, której wartość jest mniejsza niż jego położenie porządkowe w tablicy:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda

Podczas pisania lambdas, często nie trzeba określić typ parametrów wejściowych, ponieważ kompilator można wywnioskować typ na podstawie treści lambda, typy parametrów i inne czynniki, jak opisano w specyfikacji języka C#. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Jeśli kwerendy , `IEnumerable<Customer>`a następnie zmienna wejściowa jest `Customer` wnioskowany jako obiekt, co oznacza, że masz dostęp do jego metod i właściwości:  

```csharp
customers.Where(c => c.City == "London");
```

Ogólne zasady wnioskowania o typie lambdów są następujące:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.
  
Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów typowych nie ma wewnętrznego pojęcia "wyrażenia lambda". Jednak czasami wygodnie jest mówić nieformalnie o "typie" wyrażenia lambda. W takich przypadkach typ odnosi się <xref:System.Linq.Expressions.Expression> do typu delegata lub typu, na który konwertowane jest wyrażenie lambda.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Przechwytywanie zmiennych zewnętrznych i zmiennego zakresu w wyrażeniach lambda

Lambdas może odnosić się do *zmiennych zewnętrznych*. Są to zmienne, które znajdują się w zakresie w metodzie, która definiuje wyrażenie lambda lub w zakresie w typie, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano te reguły:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:  

- Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.

- Zmienne wprowadzone w wyrażeniu lambda nie są widoczne w otaczającej metody.

- Wyrażenie lambda nie może bezpośrednio przechwycić [parametru in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)lub [out](../../language-reference/keywords/out-parameter-modifier.md) z metody otaczającej.

- Instrukcja [return](../../language-reference/keywords/return.md) w wyrażeniu lambda nie powoduje, że otaczająca metoda zwraca.

- Wyrażenie lambda nie może zawierać [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md)lub [continue](../../language-reference/keywords/continue.md) instrukcji, jeśli obiekt docelowy tej instrukcji skoku znajduje się poza blokiem wyrażenia lambda. Jest to również błąd, aby instrukcja skoku poza blok wyrażenia lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Wyrażenia funkcji anonimowe](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [w specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="featured-book-chapter"></a>Polecany rozdział książki

[Delegaci, wydarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [LINQ (zapytanie zintegrowane z językiem)](../concepts/linq/index.md)
- [Drzewa wyrażeń](../concepts/expression-trees/index.md)
- [Funkcje lokalne a wyrażenia lambda](../classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [Niejawnie wpisane wyrażenia lambda](../../implicitly-typed-lambda-expressions.md)
- [Przykłady programu Visual Studio 2008 C# (zobacz przykładowe pliki zapytań LINQ i program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Rekursywne wyrażenia lambda](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)

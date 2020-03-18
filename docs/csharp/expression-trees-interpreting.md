---
title: Interpretowanie wyrażeń
description: Dowiedz się, jak napisać kod, aby sprawdzić strukturę drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 1283d7d957c72558652b96cb428efd0f071f0184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146011"
---
# <a name="interpreting-expressions"></a>Interpretowanie wyrażeń

[Poprzedni -- Wykonywanie wyrażeń](expression-trees-execution.md)

Teraz napiszmy jakiś kod, aby zbadać strukturę *drzewa wyrażeń*. Każdy węzeł w drzewie wyrażeń będzie obiektem `Expression`klasy, która pochodzi od .

Ten projekt sprawia, że odwiedzenie wszystkich węzłów w drzewie wyrażeń stosunkowo prostą operacją cykliczną. Ogólną strategią jest rozpoczęcie w węźle głównym i określenie, jaki to rodzaj węzła.

Jeśli typ węzła ma podrzędne, rekursywnie odwiedzić dzieci. W każdym węźle podrzędny powtórz proces używany w węźle głównym: określ typ, a jeśli typ ma podrzędne, odwiedź każdy z podrzędnych.

## <a name="examining-an-expression-with-no-children"></a>Badanie wyrażenia bez dzieci
Zacznijmy od ododwiedzenia każdego węzła w bardzo prostym drzewie wyrażeń.
Oto kod, który tworzy wyrażenie stałe, a następnie sprawdza jego właściwości:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Spowoduje to wydrukowanie następujących elementów:

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Teraz napiszmy kod, który zbada to wyrażenie i zapisać kilka ważnych właściwości na jego temat. Oto ten kod:

## <a name="examining-a-simple-addition-expression"></a>Badanie prostego wyrażenia dodawania

Zacznijmy od przykładu dodawania z wprowadzenia do tej sekcji.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nie używam `var` do deklarowania tego drzewa wyrażeń, ponieważ nie jest to możliwe, ponieważ po prawej stronie przypisania jest wpisywany niejawnie. Aby zrozumieć to głębiej, przeczytaj [tutaj](implicitly-typed-lambda-expressions.md).

Węzeł główny jest `LambdaExpression`. Aby uzyskać interesujący kod po prawej stronie `=>` operatora, musisz znaleźć jedno z dzieci `LambdaExpression`. Zrobimy to ze wszystkimi wyrażeniami w tej sekcji. Węzeł nadrzędny pomaga nam znaleźć typ `LambdaExpression`zwrotu pliku .

Aby sprawdzić każdy węzeł w tym wyrażeniu, musimy cyklicznie odwiedzić kilka węzłów. Oto prosta pierwsza implementacja:

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

W tym przykładzie wydrukowane są następujące dane wyjściowe:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

Zauważysz wiele powtórzeń w przykładzie kodu powyżej.
Posprzątajmy to i zbudujmy bardziej ogólnego przeznaczenia użytkownika węzła wyrażeń. To będzie wymagać od nas napisania algorytmu rekurencyjnego. Każdy węzeł może być typu, który może mieć podrzędne.
Każdy węzeł, który ma dzieci, wymaga od nas odwiedzenia tych dzieci i określenia, czym jest ten węzeł. Oto oczyszczona wersja, która wykorzystuje rekursję do odwiedzenia operacji dodawania:

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

Algorytm ten jest podstawą algorytmu, który `LambdaExpression`może odwiedzić dowolne . Istnieje wiele otworów, a mianowicie, że kod, który stworzyłem, szuka tylko bardzo małej próbki możliwych zestawów węzłów drzewa wyrażeń, które może napotkać. Jednak nadal można dowiedzieć się sporo od tego, co produkuje. (Domyślny przypadek w `Visitor.CreateFromExpression` metodzie drukuje komunikat do konsoli błędów po napotkaniu nowego typu węzła. W ten sposób wiesz, aby dodać nowy typ wyrażenia.)

Po uruchomieniu tego odwiedzającego na wyrażenie dodawania pokazane powyżej, otrzymasz następujące dane wyjściowe:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

Teraz, gdy masz bardziej ogólną implementację odwiedzających, możesz odwiedzić i przetworzyć wiele innych rodzajów wyrażeń.

## <a name="examining-an-addition-expression-with-many-levels"></a>Badanie wyrażenia dodawania z wieloma poziomami

Spróbujmy bardziej skomplikowany przykład, ale nadal ograniczyć typy węzłów tylko do dodawania:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Przed uruchomieniem tego na algorytmie odwiedzającego, spróbuj ćwiczenia myślowego, aby dowiedzieć się, co może być dane wyjściowe. Należy pamiętać, że `+` operator jest *operatorem binarnym:* musi mieć dwoje dzieci, reprezentujących lewe i prawe argumenty. Istnieje kilka możliwych sposobów konstruowania drzewa, które mogą być poprawne:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Możesz zobaczyć separację na dwie możliwe odpowiedzi, aby wyróżnić najbardziej obiecujące. Pierwszy reprezentuje *prawe wyrażenia asocjacyjne.* Drugi reprezentuje *lewych wyrażeń zesychających.*
Zaletą obu tych formatów jest to, że format jest skalowany do dowolnej liczby wyrażeń dodawania.

Jeśli to wyrażenie zostanie uruchomione przez odwiedzającego, zobaczysz to dane wyjściowe, sprawdzając, czy proste wyrażenie dodawania *pozostało zesłane.*

Aby uruchomić ten przykład i zobaczyć pełne drzewo wyrażeń, musiałem wprowadzić jedną zmianę do drzewa wyrażeń źródłowych. Gdy drzewo wyrażeń zawiera wszystkie stałe, wynikowe `10`drzewo zawiera po prostu stałą wartość . Kompilator wykonuje wszystkie dodawanie i zmniejsza wyrażenie do jego najprostszej postaci. Wystarczy dodać jedną zmienną w wyrażeniu wystarczy, aby zobaczyć oryginalne drzewo:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Utwórz odwiedzającego dla tej sumy i uruchom odwiedzającego zobaczysz to wyjście:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

Można również uruchomić dowolne inne przykłady za pomocą kodu odwiedzającego i zobaczyć, jakie drzewo reprezentuje. Oto przykład powyższego `sum3` wyrażenia (z dodatkowym parametrem, aby zapobiec kompilatorowi z obliczania stałej):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Oto dane wyjściowe od odwiedzającego:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

Należy zauważyć, że nawiasy nie są częścią danych wyjściowych. Nie ma węzłów w drzewie wyrażeń, które reprezentują nawiasy w wyrażeniu wejściowym. Struktura drzewa wyrażeń zawiera wszystkie informacje niezbędne do przekazania pierwszeństwa.

## <a name="extending-from-this-sample"></a>Rozszerzenie z tego przykładu

Przykład dotyczy tylko najbardziej prymitywnych drzew wyrazu. Kod, który widzisz w tej sekcji obsługuje tylko stałe liczby `+` całkowite i operator binarny. Jako przykład końcowy zaktualizujmy odwiedzającego, aby obsłużyć bardziej skomplikowane wyrażenie. Sprawmy, aby to działało w tym zakresie:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Ten kod reprezentuje jedną z możliwych implementacji dla funkcji *matematycznej czynników.* Sposób, w jaki napisałem ten kod, podkreśla dwa ograniczenia budowania drzew wyrażeń, przypisując wyrażenia lambda do wyrażeń. Po pierwsze, lambdas oświadczenie nie są dozwolone. Oznacza to, że nie mogę używać pętli, bloków, instrukcji if / else i innych struktur kontroli wspólnych w języku C#. Ograniczam się do używania wyrażeń. Po drugie, nie mogę rekurencyjnego wywołania tego samego wyrażenia.
Mógłbym, gdyby był już delegatem, ale nie mogę go nazwać w formie drzewa wyrazu. W sekcji na [budowanie drzew wyrażeń](expression-trees-building.md) nauczysz się technik, aby przezwyciężyć te ograniczenia.

W tym wyrażeniu napotkasz węzły wszystkich tych typów:

1. Równe (wyrażenie binarne)
2. Mnożenie (wyrażenie binarne)
3. Warunkowe (? : wyrażenie)
4. Wyrażenie wywołania `Range()` metody `Aggregate()`(wywołanie i )

Jednym ze sposobów modyfikowania algorytmu odwiedzającego jest kontynuowanie go i `default` pisanie typu węzła za każdym razem, gdy dotrzesz do klauzuli. Po kilku iteracjach zobaczysz każdy z potencjalnych węzłów. Następnie masz wszystko, czego potrzebujesz. Wynik byłby mniej więcej taki:

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

ConditionalVisitor i MethodCallVisitor przetwarzają te dwa węzły:

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

Dane wyjściowe drzewa wyrażeń będą następujące:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a>Rozszerzanie przykładowej biblioteki

Przykłady w tej sekcji pokazują podstawowych technik do odwiedzenia i zbadania węzłów w drzewie wyrażeń. I błyszczące na wiele działań może być konieczne, aby skoncentrować się na podstawowych zadań odwiedzania i uzyskiwania dostępu do węzłów w drzewie wyrażeń.

Po pierwsze, odwiedzający obsługują tylko stałe, które są liczbami całkowitymi. Stałe wartości mogą być dowolny inny typ numeryczny, a język C# obsługuje konwersje i promocje między tymi typami. Bardziej niezawodna wersja tego kodu będzie odzwierciedlać wszystkie te możliwości.

Nawet ostatni przykład rozpoznaje podzbiór możliwych typów węzłów.
Nadal można karmić go wiele wyrażeń, które spowoduje, że nie powiedzie się.
Pełna implementacja znajduje się w standardzie <xref:System.Linq.Expressions.ExpressionVisitor> .NET pod nazwą i może obsługiwać wszystkie możliwe typy węzłów.

Wreszcie, biblioteka użyłem w tym artykule został zbudowany do demonstracji i uczenia się. Nie jest zoptymalizowany. Napisałem go, aby struktury były bardzo jasne i aby podkreślić techniki używane do odwiedzania węzłów i analizowania tego, co tam jest. Implementacja produkcji zwracałaby większą uwagę na wydajność niż ja.

Nawet z tymi ograniczeniami, powinieneś być na dobrej drodze do pisania algorytmów, które czytają i rozumieją drzewa wyrażeń.

[Dalej -- Budowanie wyrażeń](expression-trees-building.md)

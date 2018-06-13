---
title: Interpretowanie wyrażenia
description: Dowiedz się, jak napisać kod, aby zbadać struktura drzewa wyrażenia.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 04622c0aa7323ac4cf16af94e31f1ef6987f87c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219313"
---
# <a name="interpreting-expressions"></a>Interpretowanie wyrażenia

[Poprzednie — Wykonywania wyrażenia](expression-trees-execution.md)

Teraz napisz kod służący do zbadania struktury *drzewo wyrażeń*. Każdy węzeł w drzewie wyrażenie będzie obiektu klasy, która jest pochodną `Expression`.

Ten projekt sprawia, że odwiedzający wszystkie węzły na drzewo wyrażenia operacji cyklicznej względnie proste do przodu. Ogólne strategii jest rozpocząć od węzła głównego i ustalić, jakiego rodzaju węzła jest.

Jeśli typ węzła ma elementy podrzędne, rekursywnie odwiedzać elementów podrzędnych. W każdym węźle podrzędnych to wielokrotnie, używane w węźle głównym: Określ typ, a jeśli typ ma elementy podrzędne, odwiedź każdego elementu podrzędnego.

## <a name="examining-an-expression-with-no-children"></a>Badanie wyrażenia bez elementów podrzędnych
Zacznijmy od odwiedzający każdy węzeł w drzewie bardzo proste wyrażenie.
Oto kod, który tworzy wyrażenie stałe, a następnie sprawdza, czy jego właściwości:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Będzie drukować następujące czynności:

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Teraz napisz kod, który będzie zbadać tego wyrażenia i zapisać niektórych właściwości ważnych informacji na ten temat. Oto kod:

## <a name="examining-a-simple-addition-expression"></a>Badanie proste wyrażenie dodanie

Zacznijmy od próbki dodanie z wprowadzenie do tej sekcji.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nie używam `var` można zadeklarować tego drzewa wyrażenia, ponieważ nie jest możliwe ponieważ prawa strona przypisania jest niejawnie wpisanych. Aby głębsze to zrozumieć, przeczytaj [tutaj](implicitly-typed-lambda-expressions.md).

Węzeł główny jest `LambdaExpression`. Aby uzyskać po prawej stronie interesującego kodu `=>` operatora, należy znaleźć jednego z elementów podrzędnych `LambdaExpression`. Firma Microsoft zrobić z wszystkie wyrażenia w tej sekcji. Węzeł nadrzędny Pomóż nam Znajdź typ zwracany `LambdaExpression`.

Do sprawdzenia każdego węzła w tym wyrażeniu, firma Microsoft będzie konieczne aby rekursywnie odwiedź stronę liczba węzłów. Oto prosty implementacji pierwszy:

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

W tym przykładzie drukowane następujące dane wyjściowe:

```
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

Można zauważyć aktualnymi w powyższym przykładzie kodu.
Umożliwia czyszczenie który i tworzenie bardziej ogólnego przeznaczenia osoba odwiedzająca węzła wyrażenia. Który będzie wymagają firmie Microsoft w celu zapisu algorytmu cyklicznego. Dowolny węzeł może być typu, który może mieć elementów podrzędnych.
Żaden węzeł, który ma elementy podrzędne musimy odwiedź te elementy podrzędne, a następnie określenie tego węzła. Oto oczyszczony zapasowej wersji, która używa rekursji do odwiedzenia operacje dodawania:

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

Ten algorytm stanowi podstawę algorytmu, które mogą odwiedzać dowolny dowolnych `LambdaExpression`. Istnieje wiele luk, czyli kod utworzoną tylko wygląda bardzo małych przykładowe możliwe zestawy węzły drzewa wyrażenia, które może on wystąpić. Jednak można wciąż uzyskać dość nieco z go tworzy. (W przypadku domyślnej `Visitor.CreateFromExpression` metoda wyświetla komunikat do konsoli błąd po napotkaniu nowego typu węzła. W ten sposób wiesz, aby dodać nowy typ wyrażenia.)

Po uruchomieniu tego obiektu odwiedzającego na wyrażeniu dodanie pokazanym powyżej można uzyskać następujące dane wyjściowe:

```
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

Teraz, bardziej ogólne implementacji obiektu odwiedzającego został utworzony, można odwiedź i przetwarzać więcej różnego rodzaju wyrażenia.

## <a name="examining-an-addition-expression-with-many-levels"></a>Badanie wyrażenie dodanie z wiele poziomów

Załóżmy spróbuj przykład bardziej skomplikowane, ale nadal Ogranicz typy węzłów można tylko dodanie:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Przed uruchomieniem tego algorytmu obiektu odwiedzającego, spróbuj wykonywania myśl, można sprawdzić, co może być dane wyjściowe. Należy pamiętać, że `+` operator jest *operatora binarnego*: musi mieć dwa elementy podrzędne, reprezentujący lewy i prawy argumentów operacji. Istnieje kilka sposobów możliwe można utworzyć drzewa, który może być poprawne:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Rozdzielenie do dwóch możliwych odpowiedzi, aby wyróżnić najbardziej obietnicy jest widoczny. Reprezentuje pierwszy *prawo asocjacyjnej* wyrażenia. Drugi reprezentują *pozostałych asocjacyjnej* wyrażenia.
Zalety obu tych dwóch formatów jest format skaluje się do dowolnej dowolne liczby dodanie wyrażenia. 

Po uruchomieniu tego wyrażenia przez obiekt odwiedzający, zobaczysz to te dane wyjściowe, weryfikowanie, czy wyrażenie proste dodanie ma *pozostałych asocjacyjnej*. 

Aby uruchomić ten przykład i Zobacz drzewa wyrażenia pełne, mają I wprowadzenie jednej zmiany źródłowe drzewo wyrażeń. Jeśli drzewo wyrażeń zawiera wszystkich stałych, wynikowe drzewo zawiera po prostu stałej wartości `10`. Kompilator wykonuje operacji dodawania i zmniejsza wyrażenie najprostszej postaci. Wystarczy dodać jednej zmiennej w wyrażeniu jest wystarczające wyświetlić oryginalne drzewa:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Utwórz obiekt odwiedzający dla tej sumy i uruchom obiekt odwiedzający zobaczysz te dane wyjściowe:

```
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

Można również uruchomić dowolne inne przykłady przez obiekt odwiedzający kod i Zobacz drzewa, które reprezentuje. Oto przykład `sum3` wyrażenie powyżej (za pomocą dodatkowej parametru aby zapobiec obliczeniowych stałą kompilatora):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Poniżej przedstawiono dane wyjściowe obiektu odwiedzającego:

```
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

Zwróć uwagę, że nawiasy nie są częścią danych wyjściowych. Nie ma żadnych węzłów w drzewie wyrażenia, reprezentujące nawiasów w wyrażeniu wejściowego. Struktura drzewa wyrażenia zawiera wszystkie informacje niezbędne do komunikowania się pierwszeństwo.

## <a name="extending-from-this-sample"></a>Rozszerzanie od tego przykładu

Przykład dotyczy tylko najbardziej podstawowe drzewa wyrażeń. Kod w tej sekcji przedstawiono obsługuje tylko stałe całkowite i plik binarny `+` operatora. Jako próbkę końcowego umożliwia aktualizacji obiekt odwiedzający do obsługi bardziej złożone wyrażenie. Upewnijmy działa w przypadku to:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Ten kod reprezentuje jedna implementacja możliwe matematyczne *silnię* funkcji. Sposób I napisanych ten kod prezentuje dwa limitiations tworzenia drzewa wyrażeń przypisując wyrażenia lambda wyrażenia. Po pierwsze instrukcji lambda nie są dozwolone. Oznacza to, nie można używać pętli, bloków, jeśli / else — instrukcje i innych kontrolowanie struktury typowe w języku C#. Jestem maksymalnie za pomocą wyrażeń. Po drugie nie można rekursywnie wywołania jednego wyrażenia.
Było to możliwe, jeśli już zostały delegata, ale nie można wywołać ją w postaci drzewa wyrażenia. W sekcji [drzew wyrażeń do kompilowania](expression-trees-building.md) dowiesz się techniki, aby wyeliminować te ograniczenia.


W tym wyrażeniu podłączania węzłów z następujących typów:
1. Równości (wyrażenie binarne)
2. Mnożenie (wyrażenie binarne)
3. Warunkowy (? : wyrażenie)
4. Wyrażenia wywołania metody (wywoływania `Range()` i `Aggregate()`)

Jednym ze sposobów zmodyfikować algorytm osoby odwiedzającej jest zachować jej wykonanie i zapisać typu węzła za każdym razem, gdy zostanie wyświetlona z `default` klauzuli. Po kilku iteracji będzie przejrzane potencjalnych węzłach. Następnie należy wymagany. Wynik będzie podobny do następującego:

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

ConditionalVisitor i MethodCallVisitor proces tych dwóch węzłów:

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

I będą dane wyjściowe dla drzewa wyrażenia:

```
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

## <a name="extending-the-sample-library"></a>Rozszerzanie biblioteki próbki

Przykłady w tej sekcji zawierają techniki core do odwiedzenia i zbadać węzłów na drzewo wyrażenia. I glossed przez wiele akcji, które mogą wymagać, aby skoncentrować się na podstawowych zadań funkcji odwiedzając i uzyskiwania dostępu do węzłów na drzewo wyrażenia. 

Po pierwsze gości obsługiwać tylko stałe, które są liczbami całkowitymi. Wartości stałe może być dowolnego typu liczbowego i języka C# obsługuje konwersje i promocji między tymi typami. Bardziej niezawodna wersja ten kod będzie duplikatów wszystkie te funkcje.

Nawet przykładu rozpoznaje podzbiór typy węzłów.
Użytkownik może nadal źródła strumieniowego go wiele wyrażeń, które spowoduje jego awarię.
Pełnego wdrożenia znajduje się w .NET Standard pod nazwą [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) i może obsługiwać wszystkie typy węzłów.

Na koniec biblioteki używane w tym artykule został utworzony dla pokazu i uczenie się. Nie jest zoptymalizowana. Napisane aby struktur oczywiste, a aby wyróżnić techniki stosowana do odwiedzenia węzły i analizowanie, co jest. Implementacji produkcyjnej może zwrócić uwagę na wydajność niż mam.

Nawet w przypadku tych ograniczeń należy również na sposób zapisywania algorytmów przeczytane i zrozumiane drzewa wyrażeń.

[Następnie — Tworzenie wyrażeń](expression-trees-building.md)

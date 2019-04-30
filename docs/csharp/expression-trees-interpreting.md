---
title: Interpreting Expressions
description: Dowiedz się, jak napisać kod, aby sprawdzić strukturę drzewa wyrażenie.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 952a1c553e2392ffc717dc344dfe77a11f025cc4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664652"
---
# <a name="interpreting-expressions"></a>Interpreting Expressions

[Poprzednie — Wykonywanie wyrażeń](expression-trees-execution.md)

Teraz umożliwia pisanie kodu w celu zbadania struktury *drzewa wyrażeń*. Każdy węzeł w drzewie wyrażeń będzie obiektem klasy, która jest pochodną `Expression`.

Ten projekt sprawia, że odwiedzający wszystkich węzłów w drzewie wyrażeń operację cyklicznego stosunkowo proste. Ogólna strategia polega na rozpoczynają się od węzła głównego i ustalić, jakiego typu węzła jest.

Jeśli typ węzła ma elementy podrzędne, rekursywnie można znaleźć elementy podrzędne. W każdym węźle podrzędnych należy powtórzyć używane w węźle głównym: Określanie typu, a jeśli typ ma elementy podrzędne, odwiedź każdego elementu podrzędnego.

## <a name="examining-an-expression-with-no-children"></a>Badanie wyrażenie żadne elementy podrzędne
Zacznijmy od, przechodząc do każdego węzła w drzewie bardzo proste wyrażenie.
Poniżej przedstawiono kod, który tworzy wyrażeniem stałym, a następnie sprawdza, czy jego właściwości:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Zostanie wydrukowany następujące czynności:

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Teraz napiszmy kod, który może zbadać to wyrażenie i zapisać niektóre ważne właściwości na jego temat. Oto kod:

## <a name="examining-a-simple-addition-expression"></a>Badanie proste wyrażenie dodawania

Zacznijmy od przykład dodawania z wprowadzeniem do tej sekcji.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nie używam `var` do deklarowania tego drzewa wyrażeń, ponieważ nie jest możliwe ponieważ po prawej stronie przypisania został niejawnie wpisany. Aby głębiej to zrozumieć, przeczytaj [tutaj](implicitly-typed-lambda-expressions.md).

Węzeł główny jest `LambdaExpression`. Aby uzyskać kod interesujące po prawej stronie `=>` operatora, należy określić jeden z elementów podrzędnych `LambdaExpression`. Możemy to zrobić za pomocą wszystkie wyrażenia w tej sekcji. Węzeł nadrzędny pomagają nam znaleźć zwracany typ `LambdaExpression`.

Aby zbadać każdego węzła w tym wyrażeniu, będzie konieczne rekursywnie odwiedza liczbę węzłów. Poniżej przedstawiono proste wdrażanie pierwszego:

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

W tym przykładzie wyświetla następujące dane wyjściowe:

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

Można zauważyć wiele powtarzających się w powyższym przykładowym kodzie.
Załóżmy, czyszczenie i tworzenia bardziej ogólnego przeznaczenia osoba odwiedzająca węzła wyrażenia. Będzie to wymagać napisać algorytm cykliczny przez firmę Microsoft. Dowolny węzeł może być typu, który może mieć elementów podrzędnych.
Dowolny węzeł, który ma elementy podrzędne wymaga od nas odwiedź te elementy podrzędne i określenie tego węzła. Oto oczyszczony wersji korzystającej z typu rekursji, aby odwiedzić operacji dodawania:

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

Ten algorytm stanowi podstawę algorytm, które mogą odwiedzać żadnych dowolnego `LambdaExpression`. Istnieje wiele powodów luki, a mianowicie szuka kod utworzoną tylko niewielką próbkę możliwe zestawy węzły drzewa wyrażenie, które może on wystąpić. Jednak nadal nauczysz dość nieco od je tworzy. (W przypadku domyślnej `Visitor.CreateFromExpression` metoda drukuje wiadomość do konsoli błędu po napotkaniu nowego typu węzła. W ten sposób możesz wiedzieć, aby dodać nowy typ wyrażenia.)

Po uruchomieniu tego obiektu odwiedzającego na wyrażenie dodawania pokazanych powyżej, możesz uzyskać następujące wyniki:

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

Teraz, gdy masz utworzoną bardziej ogólnej implementacji obiektu odwiedzającego, można znaleźć i przetwarzać wiele więcej różnych typów wyrażeń.

## <a name="examining-an-addition-expression-with-many-levels"></a>Badanie wyrażenie dodawania wielu poziomów

Teraz spróbuj bardziej skomplikowanych przykładu, ale nadal ograniczyć typy węzłów do dodawania tylko:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Przed rozpoczęciem tego algorytmu obiektu odwiedzającego, spróbuj wykonywania myślowy, określających, co może być danych wyjściowych. Należy pamiętać, że `+` operator jest *operatora binarnego*: musi mieć dwa elementy podrzędne, reprezentujący argumenty operacji po lewej i prawej stronie. Istnieje kilka sposobów możliwych do konstruowania drzewa, która może być poprawny:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Możesz zobaczyć separacji na dwa możliwe odpowiedzi, aby wyróżnić najbardziej obiecujących. Reprezentuje pierwszy *łączność do prawej strony* wyrażenia. Drugi reprezentują *łączność do lewej strony* wyrażenia.
Oba te dwa formaty zaletą jest to, czy format można skalować do dowolnego dowolną liczbę wyrażeń dodawania. 

Jeśli uruchamiasz to wyrażenie przez obiekt odwiedzający, zobaczysz następujący te dane wyjściowe weryfikacji, czy wyrażenie proste dodanie *łączność do lewej strony*. 

Aby można było uruchomić ten przykład i Zobacz drzewa pełnego wyrażenia, miałem wprowadzić zmianę w jednej na drzewo wyrażenia źródłowego. Jeśli drzewa wyrażenie zawiera wszystkich stałych, wynikowe drzewo zawiera po prostu stałej wartości `10`. Kompilator wykonuje wszystkie dodatkowe i zmniejsza wyrażenie które ma najprostszej postaci. Dodanie jednej zmiennej w wyrażeniu jest wystarczająca zobaczyć, oryginalnym drzewa:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Utwórz obiekt odwiedzający dla tej sumy, i uruchom odwiedzający zobaczysz następujące dane wyjściowe:

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

Można również uruchomić dowolne inne przykłady przez obiekt odwiedzający kod i zobacz jakie drzewa, czyli przedstawia liczbę. Oto przykład `sum3` wyrażenie powyżej (o dodatkowy parametr, aby uniemożliwić kompilatorowi obliczeń stała):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Oto dane wyjściowe obiektu odwiedzającego:

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

Należy zauważyć, że nawiasy nie są częścią danych wyjściowych. Brak żadnych węzłów w drzewie wyrażeń, które reprezentują nawiasy w wyrażenia wejściowego. Struktura drzewa wyrażenie zawiera wszystkie informacje niezbędne do komunikowania się pierwszeństwo.

## <a name="extending-from-this-sample"></a>Rozszerzanie od tego przykładu

Przykład dotyczy tylko najbardziej podstawowe drzew wyrażeń. Kod w tej sekcji przedstawiono obsługuje tylko stałych liczb całkowitych i plik binarny `+` operatora. Jako przykład końcowej zaktualizujmy obiektu odwiedzającego, aby obsłużyć bardziej skomplikowanego wyrażenia. Upewnijmy się, to działa, w tym:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Ten kod przedstawia jedna implementacja możliwe matematyczne *silnię* funkcji. Sposób moje recenzje ten kod wyróżnia dwa ograniczenia dotyczące tworzenia drzew wyrażeń, przypisując wyrażeń lambda wyrażenia. Po pierwsze instrukcji wyrażenia lambda nie są dozwolone. Oznacza to, nie można użyć pętli, bloki, jeśli / inne instrukcje i inne kontrolowanie struktury typowe w języku C#. Jestem maksymalnie za pomocą wyrażeń. Po drugie nie można rekursywnie wywołania to samo wyrażenie.
Było to możliwe, jeśli zostały już delegata, ale nie można wywołać ją w postaci drzewa wyrażeń. W sekcji [tworzenia drzew wyrażeń](expression-trees-building.md) dowiesz się, techniki, aby wyeliminować te ograniczenia.

W tym wyrażeniu spotkasz się węzły te typy:
1. Równe (wyrażenia binarnego)
2. Mnożenie (wyrażenia binarnego)
3. Warunkowy (? : wyrażenie)
4. Wyrażenia wywołania metody (wywołanie `Range()` i `Aggregate()`)

Jednym ze sposobów modyfikowania algorytm osoby odwiedzającej jest zachowania, ale wykonanie go i zapisać typu węzła za każdym razem, gdy osiągniesz swoje `default` klauzuli. Po kilku iteracjach będzie wiesz potencjalnych węzłach. Następnie masz wszystko, czego potrzebujesz. Wynik będzie podobny do poniższego:

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

I dane wyjściowe do drzewa wyrażenie będą:

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

W tej sekcji przedstawiają technik core, aby znaleźć i zbadaj węzłów na drzewo wyrażenia. Czy mogę glossed przez wiele akcji, które może być konieczne, aby można było skupić się na podstawowych zadaniach, odwiedzając i uzyskiwania dostępu do węzłów na drzewo wyrażenia. 

Po pierwsze gości obsługiwać stałe, które są liczbami całkowitymi. Stałe wartości może być dowolnego typu liczbowego, a w języku C# obsługuje konwersji i promocje między tymi typami. Bardziej niezawodna wersję ten kod będzie dublować wszystkie te funkcje.

Nawet w ostatnim przykładzie rozpoznaje podzbiór typy węzłów.
Można nadal dostarczyć on wiele wyrażeń, które spowoduje jego nie powiedzie się.
Pełną implementację znajduje się w programie .NET Standard pod nazwą <xref:System.Linq.Expressions.ExpressionVisitor> i może obsługiwać wszystkie typy węzłów.

Na koniec biblioteki używane w tym artykule została stworzona z myślą demonstracji i szkolenia. Nie jest zoptymalizowany. Napisałem, aby struktur używane oczywiste, a aby wyróżnić te techniki do odwiedzenia węzły i analizowanie, co jest. Implementacji produkcyjnej może zwrócić uwagę na wydajność nie mam.

Nawet w przypadku tych ograniczeń powinno być na dobrej drodze do pisania algorytmów przeczytać i sprawdzić drzew wyrażeń.

[Następnie — Budowanie wyrażenia](expression-trees-building.md)

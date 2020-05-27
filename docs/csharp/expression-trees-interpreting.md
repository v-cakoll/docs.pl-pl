---
title: Interpretowanie wyrażeń
description: Dowiedz się, jak napisać kod, aby sprawdzić strukturę drzewa wyrażenia.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: ea205d42b02ea7b38c04cb70d322329cf7c1d495
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004650"
---
# <a name="interpreting-expressions"></a>Interpretowanie wyrażeń

[Poprzednie--wykonywanie wyrażeń](expression-trees-execution.md)

Teraz Napiszmy kod, aby przeanalizować strukturę *drzewa wyrażenia*. Każdy węzeł w drzewie wyrażenia będzie obiektem klasy, która pochodzi od `Expression` .

Ten projekt umożliwia odwiedzanie wszystkich węzłów w drzewie wyrażenia stosunkowo prostej operacji cyklicznej. Ogólna strategia jest uruchamiana w węźle głównym i decyduje o rodzaju węzła.

Jeśli typ węzła ma elementy podrzędne, rekursywnie odwiedza elementy podrzędne. W każdym węźle podrzędnym Powtórz proces używany w węźle głównym: Określ typ, a jeśli typ ma elementy podrzędne, zapoznaj się ze wszystkimi elementami podrzędnymi.

## <a name="examining-an-expression-with-no-children"></a>Badanie wyrażenia bez elementów podrzędnych
Zacznijmy od odwiedzenia każdego węzła w prostym drzewie wyrażeń.
Oto kod, który tworzy wyrażenie stałe, a następnie analizuje jego właściwości:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Spowoduje to wydrukowanie następujących danych:

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Teraz Napiszmy kod, który będzie przebadał to wyrażenie i napisać kilka ważnych właściwości. Oto kod:

## <a name="examining-a-simple-addition-expression"></a>Badanie prostego wyrażenia dodawania

Zacznijmy od dodania przykładu od wprowadzenia do tej sekcji.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nie używam `var` do deklarowania tego drzewa wyrażenia, ponieważ nie jest to możliwe, ponieważ prawa strona przypisania jest niejawnie wpisywana.

Węzeł główny to `LambdaExpression` . Aby uzyskać interesujący kod z prawej strony `=>` operatora, należy znaleźć jeden z elementów podrzędnych `LambdaExpression` . Wykonamy te czynności ze wszystkimi wyrażeniami w tej sekcji. Węzeł nadrzędny pomaga nam znaleźć zwracany typ `LambdaExpression` .

Aby przeanalizować każdy węzeł w tym wyrażeniu, należy rekursywnie odwiedzić liczbę węzłów. Oto prosta Pierwsza implementacja:

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

Ten przykład drukuje następujące dane wyjściowe:

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

Zobaczysz wiele powtórzeń w przykładowym kodzie.
Wyczyśćmy, jak i kompilować więcej osób odwiedzających węzeł wyrażenia ogólnego przeznaczenia. Ta wartość będzie wymagała zapisania algorytmu cyklicznego. Dowolny węzeł może być typu, który może mieć elementy podrzędne.
Każdy węzeł, który ma elementy podrzędne, musi odwiedzać te elementy podrzędne i określić, czym jest ten węzeł. Oto oczyszczona wersja, która wykorzystuje rekursję do odwiedzenia operacji dodawania:

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

Ten algorytm jest podstawą algorytmu, który może odwiedzać dowolne dowolne `LambdaExpression` . Istnieje wiele otworów, co oznacza, że kod, który został utworzony, szuka bardzo małego przykładu możliwych zestawów węzłów drzewa wyrażeń, które może napotkać. Jednak nadal możesz uzyskać nieco informacji o tym, co produkuje. (Przypadek domyślny w `Visitor.CreateFromExpression` metodzie drukuje komunikat do konsoli błędów, gdy zostanie napotkany nowy typ węzła. Dzięki temu możesz dodać nowy typ wyrażenia.)

Po uruchomieniu tego gościa w wyrażeniu dodawania pokazanym powyżej otrzymujesz następujące dane wyjściowe:

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

Teraz, gdy została skompilowana bardziej ogólna implementacja gościa, można odwiedzać i przetwarzać wiele innych typów wyrażeń.

## <a name="examining-an-addition-expression-with-many-levels"></a>Badanie dodawania wyrażenia z wieloma poziomami

Wypróbujmy bardziej skomplikowany przykład, ale nadal ograniczasz typy węzłów tylko do dodawania:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Przed uruchomieniem tego polecenia w algorytmie odwiedzającym, wypróbuj ćwiczenie, aby obejść dane wyjściowe. Należy pamiętać, że `+` operator jest *operatorem binarnym*: musi mieć dwa elementy podrzędne, reprezentujący lewy i prawy operand. Istnieje kilka możliwych sposobów konstruowania drzewa, które może być poprawne:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Rozdzielenie można zobaczyć na dwie możliwe odpowiedzi, aby wyróżnić najbardziej obiecujące. Pierwsze reprezentuje wyrażenia *asocjacyjne z prawej strony* . Druga reprezentuje wyrażenia *asocjacyjne z lewej strony* .
Zaletą obu tych dwóch formatów jest skalowanie do dowolnej dowolnej liczby wyrażeń dodawania.

Jeśli to wyrażenie zostanie uruchomione za pomocą gościa, zobaczysz te dane wyjściowe, sprawdzając, czy proste wyrażenie dodawania jest *polewane*.

Aby można było uruchomić ten przykład i zobaczyć pełne drzewo wyrażeń, musiałem wprowadzić jedną zmianę w drzewie wyrażenia źródłowego. Gdy drzewo wyrażenia zawiera wszystkie stałe, utworzone drzewo po prostu zawiera stałą wartość `10` . Kompilator wykonuje wszystkie Dodawanie i zmniejsza wyrażenie do najprostszego formularza. Po prostu dodanie jednej zmiennej w wyrażeniu jest wystarczające, aby wyświetlić pierwotne drzewo:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Utwórz osobę odwiedzającą dla tej sumy i uruchom gościa, zobaczysz następujące dane wyjściowe:

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

Możesz również uruchomić dowolną z innych próbek za pomocą kodu gościa i zobaczyć, jakie drzewo reprezentuje. Oto przykład `sum3` powyższego wyrażenia (z dodatkowym parametrem uniemożliwiającym kompilatorowi Obliczanie stałej):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Oto dane wyjściowe od odwiedzających:

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

Zauważ, że nawiasy nie są częścią danych wyjściowych. W drzewie wyrażenia nie ma węzłów, które reprezentują nawiasy w wyrażeniu wejściowym. Struktura drzewa wyrażenia zawiera wszystkie informacje niezbędne do przekazania pierwszeństwa.

## <a name="extending-from-this-sample"></a>Rozszerzanie z tego przykładu

Przykład dotyczy tylko najbardziej podstawoweych drzew wyrażeń. Kod widziany w tej sekcji obsługuje tylko stałe liczby całkowite i operator binarny `+` . Jako ostatni przykład zaktualizujmy gościa, aby obsługiwał bardziej skomplikowane wyrażenie. Przyjrzyjmy się temu:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Ten kod reprezentuje jedną możliwą implementację funkcji *silnie* arytmetycznej. Sposób pisania tego kodu wyróżnia dwa ograniczenia dotyczące kompilowania drzew wyrażeń, przypisując wyrażenia lambda do wyrażeń. Najpierw wyrażenia lambda są niedozwolone. Oznacza to, że nie można używać pętli, bloków, instrukcji if/else i innych struktur formantów wspólnych w języku C#. Nie mogę używać wyrażeń. Po drugie nie można rekursywnie wywołać tego samego wyrażenia.
Mam już delegata, ale nie można go wywołać w jego formularzu drzewa wyrażeń. W sekcji dotyczącej [tworzenia drzew wyrażeń](expression-trees-building.md)należy poznać techniki, aby przezwyciężyć te ograniczenia.

W tym wyrażeniu zobaczysz węzły wszystkich następujących typów:

1. Równe (wyrażenie binarne)
2. Pomnóż (wyrażenie binarne)
3. Warunkowo (? wyrażenia
4. Wyrażenie wywołania metody (wywoływanie `Range()` i `Aggregate()` )

Jednym ze sposobów modyfikowania algorytmu gościa jest zachowanie go i zapisanie typu węzła za każdym razem, gdy docierasz do `default` klauzuli. Po kilku iteracjach zobaczysz każdy z potencjalnych węzłów. Następnie masz wszystko, co jest potrzebne. Wynik będzie wyglądać następująco:

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

Proces ConditionalVisitor i MethodCallVisitor te dwa węzły:

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

A dane wyjściowe dla drzewa wyrażenia:

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

## <a name="extending-the-sample-library"></a>Rozszerzanie biblioteki przykładowej

W przykładach w tej sekcji przedstawiono podstawowe techniki do odwiedzania i sprawdzenia węzłów w drzewie wyrażenia. Mam wiele akcji, które mogą być potrzebne, aby skoncentrować się na podstawowych zadaniach związanych z odwiedzaniem i uzyskiwaniem dostępu do węzłów w drzewie wyrażenia.

Najpierw Goście obsługują tylko stałe, które są liczbami całkowitymi. Stałe wartości mogą być dowolnego innego typu liczbowego, a język C# obsługuje konwersje i promocje między tymi typami. Bardziej niezawodna wersja tego kodu będzie dublować wszystkie te funkcje.

Nawet ostatni przykład rozpoznaje podzestaw możliwych typów węzłów.
Nadal można uzyskać wiele wyrażeń, które spowodują niepowodzenie.
Pełna implementacja jest uwzględniona w .NET Standard pod nazwą <xref:System.Linq.Expressions.ExpressionVisitor> i może obsługiwać wszystkie możliwe typy węzłów.

Na koniec Biblioteka użyta w tym artykule została skompilowana w celu pokazania i uczenia się. Nie została zoptymalizowana. Ja został napisany, aby określić, że struktury są używane, i podświetlić techniki używane do odwiedzania węzłów i przeanalizować zawartość. Implementacja produkcyjna zwróci więcej uwagi na wydajność niż mam.

Nawet z tymi ograniczeniami, należy być dobrym sposobem pisania algorytmów, które odczytują i opisują drzewa wyrażeń.

[Następne — tworzenie wyrażeń](expression-trees-building.md)

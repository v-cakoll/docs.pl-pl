---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak odwiedzać każdy węzeł w drzewie wyrażenia podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażenia.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: b3c575876b6d53e9db366f59ad45aac714923c45
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202952"
---
# <a name="translating-expression-trees"></a>Tłumaczenie drzew wyrażeń

[Poprzednie — Kompilowanie wyrażeń](expression-trees-building.md)

W tej ostatniej sekcji dowiesz się, jak odwiedzać każdy węzeł w drzewie wyrażenia podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażenia. Są to techniki, które będą używane w dwóch ważnych scenariuszach. Pierwszy polega na zrozumieniu algorytmów wyrażonych przez drzewo wyrażenia, aby można było je przetłumaczyć na inne środowisko. Druga jest zmiana algorytmu, który został utworzony. Może to być dodanie rejestrowania, wywołanie metody przechwytywania i śledzenie ich lub inne cele.

## <a name="translating-is-visiting"></a>Trwa odwiedzanie tłumaczenia

Kod, który tworzysz w celu przetłumaczenia drzewa wyrażenia, jest rozszerzeniem tego, co już widzisz, aby odwiedzić wszystkie węzły w drzewie. W przypadku tłumaczenia drzewa wyrażenia odwiedzane są wszystkie węzły, a podczas odwiedzania można utworzyć nowe drzewo. Nowe drzewo może zawierać odwołania do oryginalnych węzłów lub nowe węzły, które zostały umieszczone w drzewie.

Zobaczmy to w akcji, odwiedzając drzewo wyrażenia i tworząc nowe drzewo z niektórymi węzłami zastępczymi. W tym przykładzie zamienimy każdą stałą na stałą o dziesięć razy większym.
W przeciwnym razie pozostawimy drzewo wyrażenia bez zmian. Zamiast odczytywania wartości stałej i zamieniania jej na nową stałą, wprowadzimy tę zamianę, zastępując węzeł stały nowym węzłem, który wykonuje mnożenie.

W tym miejscu po znalezieniu stałego węzła utworzysz nowy węzeł mnożenia, którego elementy podrzędne są pierwotną stałą i stałą `10`:

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

Zastępując pierwotny węzeł podstawianiem, tworzone jest nowe drzewo zawierające nasze modyfikacje. Możemy sprawdzić, czy przez skompilowanie i wykonanie zastąpionego drzewa.

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

Tworzenie nowego drzewa jest kombinacją odwiedzanych węzłów w istniejącym drzewie i tworzenie nowych węzłów i wstawianie ich do drzewa.

Ten przykład pokazuje ważność drzew wyrażeń, które są niezmienne. Należy zauważyć, że nowe drzewo utworzone powyżej zawiera kombinację nowo utworzonych węzłów i węzłów z istniejącego drzewa. Jest to bezpieczne, ponieważ nie można modyfikować węzłów w istniejącym drzewie. Może to spowodować znaczne zwiększenie wydajności pamięci.
Te same węzły można używać w całym drzewie lub w wielu drzewach wyrażeń. Ponieważ węzły nie mogą być modyfikowane, ten sam węzeł może być ponownie używany w dowolnym momencie.

## <a name="traversing-and-executing-an-addition"></a>Przechodzenie i wykonywanie dodawania

Sprawdźmy to, tworząc drugiego odwiedzającego, który przeprowadzi drzewo węzłów dodawania i obliczy wynik. Można to zrobić, wprowadzając kilka modyfikacji odwiedzanych do tej pory. W tej nowej wersji odwiedzający zwróci częściową sumę operacji dodawania do tego punktu. Wyrażenie stałe, które jest po prostu wartością wyrażenia stałej. W przypadku wyrażenia dodawania wynik jest sumą argumentów operacji lewy i prawy, gdy te drzewa zostały przesunięte.

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

W tym miejscu jest dość dużo kodu, ale koncepcje są bardzo podejścia.
Ten kod wizytuje elementy podrzędne na głębokości pierwszego wyszukiwania. Gdy napotka węzeł stały, odwiedzający zwraca wartość stałej. Po odwiedzeniu obu elementów podrzędnych osoby odwiedzające będą obliczać sumę obliczoną dla tego poddrzewa. Węzeł dodawania może teraz obliczyć jego sumę.
Po odwiedzeniu wszystkich węzłów w drzewie wyrażenia suma zostanie obliczona. Wykonanie można śledzić przez uruchomienie przykładu w debugerze i śledzenie wykonania.

Ułatwiamy śledzenie sposobu analizowania węzłów i sposobu obliczania sumy przez przechodzenie przez drzewo. Oto zaktualizowana wersja metody agregującej, która zawiera dość kilka informacji o śledzeniu:

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

Uruchomienie go w tym samym wyrażeniu daje następujące dane wyjściowe:

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

Śledź dane wyjściowe i postępuj zgodnie z powyższym kodem. Powinien być w stanie dowiedzieć się, jak kod odwiedza każdy węzeł i oblicza sumę w miarę przechodzenia przez drzewo i odnajduje sumę.

Teraz przyjrzyjmy się różnemu przebiegowi z wyrażeniem podanym przez `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Oto dane wyjściowe badania tego wyrażenia:

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

Gdy ostateczna odpowiedź jest taka sama, przechodzenie drzewa jest zupełnie inne. Węzły są przesyłane w innej kolejności, ponieważ drzewo zostało skonstruowane z różnymi operacjami wykonywanymi jako pierwsze.

## <a name="learning-more"></a>Więcej informacji

Ten przykład pokazuje mały podzbiór kodu, który będzie przepływał i interpretuje algorytmy reprezentowane przez drzewo wyrażenia. Aby uzyskać kompletną dyskusję na temat wszystkich zadań niezbędnych do utworzenia biblioteki ogólnego przeznaczenia, która tłumaczy drzewa wyrażeń na inny język, Przeczytaj [tę serię](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) przez otoczkę Warren. Szczegółowe informacje na temat sposobu tłumaczenia dowolnego kodu, który może znajdować się w drzewie wyrażenia.

Mam nadzieję, że już widzisz prawdziwą moc drzew wyrażeń.
Możesz sprawdzić zestaw kodu, wprowadzić wszelkie zmiany w tym kodzie i wykonać zmienioną wersję. Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowe drzewa przy użyciu składników istniejących drzew. Minimalizuje to ilość pamięci wymaganej do utworzenia zmodyfikowanych drzew wyrażeń.

[Następne — sumowanie](expression-trees-summary.md)

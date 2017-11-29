---
title: "Tłumaczenie drzew wyrażeń"
description: "Dowiedz się, jak można znaleźć każdy węzeł w drzewie wyrażeń podczas kompilowania zmodyfikowane kopię tego drzewa wyrażenia."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 602a17591d27ebfd098516453b9028bca37ad5e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="translating-expression-trees"></a>Tłumaczenie drzew wyrażeń

[Poprzednie — Tworzenie wyrażeń](expression-trees-building.md)

W tej sekcji końcowego dowiesz się, jak do odwiedzenia każdy węzeł w drzewie wyrażeń podczas kompilowania zmodyfikowane kopię tego drzewa wyrażenia. Są to te techniki, które będą używane w przypadku dwóch scenariuszy ważne. Pierwsza to zrozumienie algorytmów wyrażone w drzewo wyrażenia, dzięki czemu można można przetłumaczyć innego środowiska. Drugim jest, jeśli chcesz zmienić algorytmu, który został utworzony. Może to być dodać rejestrowania, przechwycenia wywołania metody i śledzenie ich lub innych celów.

## <a name="translating-is-visiting"></a>Tłumaczenie odwiedzania

Kod kompilacji do drzewa wyrażeń przetłumaczenia jest rozszerzeniem co już w tym samouczku odwiedzać wszystkich węzłów w drzewie. Tłumaczenie drzewo wyrażenia, odwiedź stronę wszystkich węzłów, a podczas odwiedzania je, należy utworzyć nowe drzewo. Nowe drzewo może zawierać odwołania do oryginalnego węzłów lub nowe węzły, które zostały umieszczone w drzewie.

Zobaczmy, to w akcji odwiedzając drzewo wyrażeń i tworzenia nowego drzewa węzły zastąpienia. W tym przykładzie załóżmy Zamień wszystkie stała stałą dziesięć razy większy.
W przeciwnym razie pozostanie drzewa wyrażenia bez zmian. Zamiast odczytu wartości stałej i zastępowanie stałą nowe, wybierzemy zamiany przez zamianę stałej węzła nowego węzła, który wykonuje mnożenia.

W tym miejscu po znalezieniu stałej węzła tworzenia nowego węzła mnożenia, którego elementy podrzędne są oryginalne stała i stałą `10`:

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

Przez zastąpienie oryginalnego węzła podstaw, nowe drzewo został uformowany zawierający naszych modyfikacje. Firma Microsoft może Sprawdź, czy kompilowanie i wykonywania zastąpionego drzewa.

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

Tworzenie nowego drzewa jest kombinacją odwiedzając węzłów w drzewie istniejących i tworzenia nowych węzłów i wstawianie ich do drzewa.

Ten przykład przedstawia znaczenie jest niezmienialny drzewa wyrażeń. Należy zauważyć, że nowe drzewo utworzone powyżej zawiera węzły nowo utworzona i węzłów z istniejącego drzewa. To bezpieczne, ponieważ nie można zmodyfikować węzłów w drzewie istniejących. Może to spowodować pamięci znaczących korzyści.
W drzewie lub w wielu drzew wyrażeń można tych samych węzłów. Ponieważ nie można modyfikować, może być tym samym węźle ponownie po każdej zmianie jego uruchomienie.

## <a name="traversing-and-executing-an-addition"></a>Przeglądanie i wykonywania dodatku

Umożliwia to sprawdzić, tworząc drugi obiekt odwiedzający, który przegląda drzewo dodawania węzłów i oblicza wynik. Można to zrobić przez kilka vistor, który w tym samouczku wykonanej do tej pory. W tej nowej wersji obiektu odwiedzającego zwróci sumy częściowe operacja dodawania do tego punktu. Wyrażenie stałe jest po prostu wartość wyrażenia stałej. Dla wyrażenia dodanie wynik to suma argumentów operacji lewy i prawy po przejść wzdłuż tych drzew.

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

Występuje dość nieco tutaj kod, ale pojęcia są bardzo przystępne.
Ten kod odwiedza dzieci w wyszukiwaniu pierwszy głębokość. Po napotkaniu stałej węzła obiektu odwiedzającego zwraca wartość stałej. Po obiekt odwiedzający odwiedził obu elementów podrzędnych, te dzieci będzie obliczana sum obliczonych dla tego poddrzewa. Dodawanie węzła teraz można obliczyć jego sum.
Po odwiedzone wszystkie węzły na drzewo wyrażenia, Suma zostanie obliczone. Można śledzić realizację uruchamiając próbki w debugerze i śledzenie realizacji.

Załóżmy ułatwić śledzenie jak są analizowane węzły i jak suma jest obliczana przez travsersing drzewa. W tym miejscu jest zaktualizowana wersja metoda agregacji, która zawiera dość bit informacje śledzenia:

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

Uruchomienie jej w tym samym wyrażeniu daje następujące dane wyjściowe:

```
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

Dane wyjściowe śledzenia i odbiorze w powyższym kodzie. Można będzie działać jak kod odwiedza każdego węzła i oblicza sumę, ponieważ przechodzi przez drzewa i wyszukuje suma.

Teraz Przyjrzyjmy różnych Uruchom za pomocą wyrażenia przez `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Poniżej przedstawiono dane wyjściowe z badanie tego wyrażenia:

```
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

Podczas końcowego odpowiedzi są takie same, całkowicie różni się przechodzenia drzewa. Węzły są pokonać w innej kolejności, ponieważ drzewa został skonstruowany przy różnych operacji wykonywanych w pierwszym.

## <a name="learning-more"></a>Dowiedzieć się więcej

W tym przykładzie pokazano małego podzbioru kod, który będzie kompilacji do przechodzenia i interpretowania algorytmów reprezentowany przez drzewo wyrażenia. Aby uzyskać szczegółowe omówienie pracy niezbędne do tworzenia biblioteki ogólnego przeznaczenia, który tłumaczy drzew wyrażeń do innego języka, przeczytaj [tej serii](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) przez Matt Warren. Przechodzi ona bardzo szczegółowe na temat sposobu tłumaczenia kodu, jakie można znaleźć w drzewo wyrażenia.

Mam nadzieję, że obecnie w tym samouczku true możliwości drzewa wyrażeń.
Można zbadać zestawu kodu, wprowadź wszelkie zmiany, które chcesz do kodu i wykonaj zmienionych wersji. Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowego drzew przy użyciu składników istniejącego drzewa. Pozwala to zmniejszyć ilość pamięci potrzebnej do tworzenia drzewa wyrażeń zmodyfikowane.

[Następnie — Podsumowanie](expression-trees-summary.md)

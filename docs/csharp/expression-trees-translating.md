---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak odwiedzić każdy węzeł w drzewie wyrażeń podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76115775"
---
# <a name="translate-expression-trees"></a>Przetłumacz drzewa wyrażeń

[Poprzedni -- Budowanie wyrażeń](expression-trees-building.md)

W tej ostatniej sekcji dowiesz się, jak odwiedzić każdy węzeł w drzewie wyrażeń podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażeń. Są to techniki, które będą używane w dwóch ważnych scenariuszach. Pierwszym z nich jest zrozumienie algorytmów wyrażonych przez drzewo wyrażeń, dzięki czemu można je przetłumaczyć na inne środowisko. Drugi to, kiedy chcesz zmienić algorytm, który został utworzony. Może to być dodanie rejestrowania, przechwytywania wywołań metody i śledzenie ich lub innych celów.

## <a name="translating-is-visiting"></a>Tłumaczenie polega na odwiedzeniu

Kod, który tworzysz w celu przetłumaczenia drzewa wyrażeń jest rozszerzeniem tego, co już widziałeś, aby odwiedzić wszystkie węzły w drzewie. Po przetłumaczeniu drzewa wyrażeń, odwiedź wszystkie węzły i podczas ich wizyty, zbudować nowe drzewo. Nowe drzewo może zawierać odwołania do oryginalnych węzłów lub nowe węzły, które zostały umieszczone w drzewie.

Zobaczmy to w akcji, odwiedzając drzewo wyrażeń i tworząc nowe drzewo z niektórymi węzłami zastępczymi. W tym przykładzie zastąpmy dowolną stałą stałą, która jest dziesięć razy większa.
W przeciwnym razie pozostawimy drzewo wyrażeń nienaruszone. Zamiast odczytywać wartość stałej i zastępować ją nową stałą, dokonamy tego zastąpienia, zastępując węzeł stały nowym węzłem, który wykonuje mnożenie.

W tym miejscu po znalezieniu stałego węzła można utworzyć nowy węzeł mnożenia, `10`którego podrzędne są oryginalną stałą, a stała:

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

Zastępując oryginalny węzeł substytutem, powstaje nowe drzewo, które zawiera nasze modyfikacje. Możemy to sprawdzić, kompilując i wykonując zastąpione drzewo.

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

Tworzenie nowego drzewa jest kombinacją odwiedzania węzłów w istniejącym drzewie i tworzenia nowych węzłów i wstawiania ich do drzewa.

W tym przykładzie pokazano znaczenie drzewa wyrażenie jest niezmienne. Należy zauważyć, że nowe drzewo utworzone powyżej zawiera mieszaninę nowo utworzonych węzłów i węzłów z istniejącego drzewa. Jest to bezpieczne, ponieważ węzłów w istniejącym drzewie nie można modyfikować. Może to spowodować znaczną wydajność pamięci.
Te same węzły mogą być używane w całym drzewie lub w wielu drzewach wyrażeń. Ponieważ węzłów nie można modyfikować, ten sam węzeł może być ponownie użyty, gdy jest to potrzebne.

## <a name="traversing-and-executing-an-addition"></a>Przechodzenie przez i wykonywanie dodawania

Sprawdźmy to, budując drugiego odwiedzającego, który przechodzi przez drzewo węzłów dodawania i oblicza wynik. Możesz to zrobić, dokonując kilku modyfikacji dla odwiedzającego, który widziałeś do tej pory. W tej nowej wersji użytkownik zwróci częściową sumę operacji dodawania do tego momentu. Dla wyrażenia stałego jest to po prostu wartość wyrażenia stałego. Dla wyrażenia dodawania wynik jest sumą lewego i prawego argumentów, gdy te drzewa zostały przeciągnięte.

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

Jest tu sporo kodu, ale pojęcia są bardzo przystępne.
Ten kod odwiedza dzieci w dogłębnym pierwszym wyszukiwaniu. Gdy napotka węzeł stały, gość zwraca wartość stałej. Po użytkownik odwiedził oba dzieci, te dzieci będą obliczać sumę obliczoną dla tego poddrzewa. Węzeł dodawania można teraz obliczyć jego sumę.
Po odwiedzeniu wszystkich węzłów w drzewie wyrażeń suma zostanie obliczona. Można śledzić wykonanie, uruchamiając przykład w debugerze i śledzenia wykonania.

Ułatwiamy śledzenie, jak węzły są analizowane i jak suma jest obliczana przez przechodzenie przez drzewo. Oto zaktualizowana wersja metody Agreguj, która zawiera sporo informacji o śledzeniu:

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

Uruchomienie go na tym samym wyrażeniu daje następujące dane wyjściowe:

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

Śledzenie danych wyjściowych i postępuj zgodnie z powyższym kodem. Powinieneś być w stanie ustalić, jak kod odwiedza każdy węzeł i oblicza sumę, jak przechodzi przez drzewo i znajduje sumę.

Teraz przyjrzyjmy się innemu przebiegowi, `sum1`z wyrażeniem podanym przez:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Oto dane wyjściowe z badania tego wyrażenia:

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

Podczas gdy ostateczna odpowiedź jest taka sama, przechodzenie drzewa jest zupełnie inna. Węzły są przemieszczane w innej kolejności, ponieważ drzewo zostało zbudowane z różnych operacji występujących najpierw.

## <a name="learning-more"></a>Dodatkowe informacje

W tym przykładzie przedstawiono mały podzbiór kodu, który można utworzyć do przechodzenia i interpretować algorytmy reprezentowane przez drzewo wyrażeń. Aby uzyskać pełną dyskusję na temat wszystkich prac niezbędnych do zbudowania biblioteki ogólnego przeznaczenia, która tłumaczy drzewa wyrażeń na inny język, przeczytaj [tę serię autorstwa](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) Matta Warrena. Przechodzi do bardzo szczegółowo, jak przetłumaczyć dowolny kod, który można znaleźć w drzewie wyrażeń.

Mam nadzieję, że widzieliście teraz prawdziwą moc drzew ekspresji.
Można sprawdzić zestaw kodu, wprowadzić wszelkie zmiany, które chcesz do tego kodu i wykonać zmienioną wersję. Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowe drzewa przy użyciu składników istniejących drzew. Minimalizuje to ilość pamięci potrzebnej do utworzenia drzew wyrażeń zmodyfikowanych.

[Dalej -- Podsumowując](expression-trees-summary.md)

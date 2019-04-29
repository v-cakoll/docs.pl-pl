---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak znaleźć każdy węzeł w drzewie wyrażeń podczas kompilowania zmodyfikowanej kopii takiego drzewa wyrażeń.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 4c14837c1d92845991d8ea9990b77eb9052757d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646556"
---
# <a name="translating-expression-trees"></a>Tłumaczenie drzew wyrażeń

[Poprzednie — Tworzenie wyrażeń](expression-trees-building.md)

W tej sekcji końcowej dowiesz się, jak do odwiedzenia każdego węzła w drzewie wyrażeń podczas kompilowania zmodyfikowanej kopii takiego drzewa wyrażeń. Są to technik, które będą używane w przypadku dwóch scenariuszy ważne. Pierwszy to zrozumienie algorytmy wyrażona przez drzewo wyrażenia, dzięki czemu mogą być tłumaczone w innym środowisku. Drugim jest, jeśli chcesz zmienić algorytmu, który został utworzony. Może to być dodawanie rejestrowania przechwytuje wywołania metody oraz śledzić ich lub innych celów.

## <a name="translating-is-visiting"></a>Tłumaczenie jest odwiedzający

Kod kompilacji do translacji drzewa wyrażenie jest rozszerzeniem już opisane do odwiedzenia wszystkich węzłów w drzewie. Tłumaczenie jest drzewo wyrażenia, odwiedź stronę wszystkie węzły, a podczas odwiedzania ich, tworzenie nowego drzewa. Nowe drzewo może zawierać odwołania do oryginalnego węzłów lub nowe węzły, które zostały umieszczone w drzewie.

Zobaczmy, to w działaniu strony drzewo wyrażenia, tworzenie nowego drzewa węzły zastępczy. W tym przykładzie Przyjrzyjmy zastąpić dowolną stałą ze stałą, której jest dziesięć razy większy.
W przeciwnym razie pozostawimy drzewa wyrażeń bez zmian. Zamiast odczytu wartości stałej i zamianę stałą nowe, My sprawiamy, żeby ta zastępowania, zastępując stałej węzła nowy węzeł, który wykonuje mnożenia.

W tym miejscu po odnalezieniu stałej węzła tworzysz nowy węzeł mnożenia, którego elementy podrzędne są oryginalne stała i stałą `10`:

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

Przez zastąpienie pierwotnego węzła zastępczych, nowego drzewa, tworzy zawiera modyfikacje. Zweryfikowanie, kompilując i wykonywania drzewie zastąpione.

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

Tworzenie nowego drzewa jest kombinacją odwiedzający węzły w istniejącym drzewie i tworzenia nowych węzłów i wstawiania ich do drzewa.

W tym przykładzie przedstawiono znaczenie drzew wyrażeń, które są niezmienne. Należy zauważyć, że nowe drzewo utworzonego powyżej zawiera kombinację nowo utworzony węzłów i węzłów z istniejącym drzewie. To bezpieczne, ponieważ nie można zmodyfikować węzły w istniejącym drzewie. Może to spowodować, że pamięć znaczne korzyści.
Tym samym węzłów może służyć w całym drzewie lub w wielu drzewach wyrażeń. Ponieważ nie można modyfikować, tego samego węzła może być ponownie użyte w każdym przypadku, gdy jego potrzebne.

## <a name="traversing-and-executing-an-addition"></a>Przeglądanie i wykonywanie dodatku

Możemy to sprawdzić, tworząc drugi obiekt odwiedzający, który przegląda drzewo dodawania węzłów i oblicza wynik. Można to zrobić, wprowadzając kilka zmian obiekt odwiedzający, który w tym samouczku do tej pory. W tej nowej wersji odwiedzający zwróci częściowej sumy operacji dodawania do tej pory. Wyrażenie stałe to po prostu wartość wyrażenie stałe. Wyrażenie dodawania wynik jest sumę argumentów operacji po lewej i prawej stronie, gdy-przenoszone tych drzew.

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

Brak znacznej liczby tutaj kod, ale podstawowe koncepcje są bardzo przystępne.
Ten kod odwiedza dzieci w wyszukiwaniu pierwszy głębi. Po napotkaniu stałej węzła, odwiedzający zwraca wartość stałej. Po użytkownik odwiedził oba elementy podrzędne, te elementy podrzędne zostanie obliczona suma obliczana dla tego poddrzewa. Dodawanie węzła teraz można obliczyć jego sum.
Po odwiedzone wszystkich węzłów w drzewie wyrażeń suma zostaną obliczone. Uruchamianie przykładu w debugerze i śledzenie wykonywania można śledzić wykonywanie.

Spróbujmy ułatwiają śledzenie sposobu węzły są analizowane i jak suma jest obliczana przez przechodzenie drzewa. Oto zaktualizowaną wersję metoda agregacji, która obejmuje znacznej liczby informacji śledzenia:

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

Uruchomiony na tym samym wyrażeniu daje następujące wyniki:

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

Dane wyjściowe śledzenia i kontynuować pracę w powyższym kodzie. Powinien móc wyglądają jak kod odwiedza każdy węzeł i oblicza sumę przechodzi przez drzewo i wyszukuje sumy.

Teraz Przyjrzyjmy się inny przebieg, za pomocą wyrażenia określone przez `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Oto dane wyjściowe sprawdzając to wyrażenie:

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

Mimo że końcowy odpowiedź jest taka sama, przechodzenie drzewa jest całkowicie inny. Węzły są w czasie podróży w innej kolejności, ponieważ drzewie został skonstruowany przy użyciu różnych operacji występujących najpierw.

## <a name="learning-more"></a>Dowiedz się więcej

Niniejszy przykład pokazuje mały podzbiór kod, który tworzysz przechodzenia i interpretować algorytmów, reprezentowane przez drzewo wyrażenia. Szczegółowe omówienie pracy niezbędne do tworzenia biblioteki ogólnego przeznaczenia, która przekształca drzew wyrażeń w innym języku, należy przeczytać [tę serię](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) przez Matt Warren. Przechodzi ona bardzo szczegółowe na temat sposobu translacji kodu, które mogą okazać się w drzewie wyrażeń.

Mam nadzieję, że teraz w tym samouczku prawdziwą moc drzew wyrażeń.
Można zbadać zestawu kodu, wprowadź zmiany, które chcesz do tego kodu i wykonaj zmienionych wersji. Ponieważ drzew wyrażeń są niezmienne, można utworzyć nowego drzewa, przy użyciu składników istniejących drzew. Zmniejsza to ilość pamięci wymaganej do tworzenia drzew wyrażeń zmodyfikowane.

[Następnie — Podsumowanie](expression-trees-summary.md)

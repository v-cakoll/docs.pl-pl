---
title: Typy platform obsługujące drzewa wyrażeń
description: Poznaj typy struktur obsługujące drzewa wyrażeń, tworzenie drzew wyrażeń i techniki umożliwiające pracę z interfejsami API drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 157e97594f27345ac96fe91f7dd6f29907c2c7ac
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037619"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy platform obsługujące drzewa wyrażeń

[Opisane wcześniej drzewa wyrażeń](expression-trees-explained.md)

Istnieje duża lista klas w programie .NET Core Framework, które współpracują z drzewami wyrażeń.
Pełną listę można znaleźć pod adresem <xref:System.Linq.Expressions>.
Zamiast korzystać z pełnej listy, przyjrzyjmy się, jak zostały zaprojektowane klasy struktury.

W projekcie języka wyrażenie jest treścią kodu, który oblicza i zwraca wartość. Wyrażenia mogą być bardzo proste: wyrażenie stałe `1` zwraca wartość stałą 1. Mogą być bardziej skomplikowane: wyrażenie `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` zwraca jeden element główny dla równania kwadratowego (w przypadku, gdy równanie ma rozwiązanie).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Wszystko zaczyna się od system. LINQ. Expression

Jedną z złożoności pracy z drzewami wyrażeń jest to, że wiele różnych rodzajów wyrażeń jest prawidłowych w wielu miejscach w programach. Rozważ wyrażenie przypisania. Prawa strona przypisania może być wartością stałą, zmienną, wyrażeniem wywołania metody lub innymi. Ta elastyczność języka oznacza, że podczas przechodzenia drzewa wyrażenia mogą wystąpić wiele różnych typów wyrażeń w dowolnym miejscu w węzłach drzewa. W związku z tym, jeśli można korzystać z typu wyrażenia podstawowego, jest to najprostszy sposób na działanie. Jednak czasami trzeba dowiedzieć się więcej.
Klasa wyrażenie podstawowe zawiera właściwość `NodeType` do tego celu.
Zwraca `ExpressionType`, który jest wyliczeniem możliwych typów wyrażeń.
Po poznaniu typu węzła można rzutować go na ten typ, a następnie wykonywać określone akcje, znając typ węzła wyrażenia. Można wyszukiwać określone typy węzłów, a następnie korzystać z określonych właściwości tego rodzaju wyrażenia.

Na przykład ten kod będzie drukował nazwę zmiennej dla wyrażenia dostępu do zmiennej. Po wykonaniu tych wskazówek zawarto sprawdzanie typu węzła, a następnie rzutowanie na wyrażenie dostępu do zmiennej, a następnie Sprawdzanie właściwości konkretnego typu wyrażenia:

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a>Tworzenie drzew wyrażeń

Klasa `System.Linq.Expression` zawiera również wiele metod statycznych do tworzenia wyrażeń. Te metody tworzą węzeł wyrażenia przy użyciu argumentów dostarczonych dla jego elementów podrzędnych. W ten sposób utworzysz wyrażenie na podstawie jego węzłów liścia. Na przykład ten kod kompiluje wyrażenie Add:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

W tym prostym przykładzie można zobaczyć, że wiele typów obejmuje tworzenie i pracę z drzewami wyrażeń. Ta złożoność jest niezbędna do zapewnienia możliwości rozbudowanego słownictwa dostarczonego przez C# język.

## <a name="navigating-the-apis"></a>Nawigowanie po interfejsach API
Istnieją typy węzłów wyrażeń, które mapują do niemal wszystkich elementów składni C# języka. Każdy typ ma określone metody dla tego typu elementu języka. Jest to bardzo dużo do utrzymania w Twoim głowie. Zamiast próbować znają wszystko, Oto techniki używane do pracy z drzewami wyrażeń:

1. Sprawdź elementy członkowskie wyliczenia `ExpressionType`, aby określić możliwe węzły, które należy sprawdzić. Jest to naprawdę pomocne, gdy chcesz przechodzenie i zrozumieć drzewo wyrażeń.
2. Sprawdź statyczne elementy członkowskie klasy `Expression`, aby utworzyć wyrażenie. Metody te mogą tworzyć dowolne typy wyrażeń z zestawu jego węzłów podrzędnych.
3. Przyjrzyj się klasie `ExpressionVisitor`, aby utworzyć zmodyfikowane drzewo wyrażeń.

Dowiesz się więcej na temat każdego z tych trzech obszarów. Niezmiennie, czego potrzebujesz, gdy rozpoczniesz pracę z jednym z tych trzech kroków.
 
 [Następne--wykonywanie drzew wyrażeń](expression-trees-execution.md)

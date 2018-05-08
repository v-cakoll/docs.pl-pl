---
title: Framework typy obsługi drzewa wyrażeń
description: Informacje o typach framework obsługi drzewa wyrażeń tworzenia drzewa wyrażeń i techniki pracy z drzewa wyrażenia interfejsów API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 3110f2a9534085aba95fcb5c8e76f66229e79f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="framework-types-supporting-expression-trees"></a>Framework typy obsługi drzewa wyrażeń

[Poprzedniej — Wyjaśniono drzew wyrażeń](expression-trees-explained.md)

Brak obszerne listy klas w ramach platformy .NET Core, które współpracują z drzewa wyrażeń.
Można zapoznać się z pełną listą [tutaj](/dotnet/core/api/System.Linq.Expressions).
Zamiast uruchamiania za pomocą z pełną listą, Przyjrzyjmy się, jak zostały zaprojektowane klasy framework.

W języku wyrażenie jest treści kodu, który oblicza i zwraca wartość. Wyrażenia może być bardzo prosta: wyrażenie stałe `1` zwraca stała wartość 1. Może być bardziej skomplikowane: wyrażenie `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` zwraca jeden katalog główny dla kwadratowe równości (w przypadku, gdy równanie ma rozwiązania).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Rozpoczyna się System.Linq.Expression

Jednym z złożonością, Praca z drzewa wyrażeń jest różne rodzaje wyrażeń są prawidłowe w wielu miejscach w programach. Należy wziąć pod uwagę wyrażenia przypisania. Po prawej stronie przypisania może być wartością stałą, zmienną, wyrażenie wywołania metody lub innych użytkowników. Ten język elastyczność oznacza, mogą wystąpić wiele typów różnych wyrażenie w dowolnym miejscu węzły drzewa przechodzenie drzewo wyrażenia. W związku z tym podczas pracy z typem wyrażenia podstawowego, który jest najprostszym sposobem pracy. Czasami potrzebny dowiedzieć się więcej.
Klasa podstawowa wyrażenie zawiera `NodeType` właściwości w tym celu.
Zwraca `ExpressionType` czyli wyliczenie typów możliwy wyrażeniu.
Po sprawdzeniu typ węzła rzutowania go do tego typu, a wykonywanie określonych czynności, które wiedząc typ węzła wyrażenia. Wyszukiwanie niektórych typów węzłów i następnie pracować z określone właściwości typu wyrażenia.

Na przykład ten kod będzie drukować nazwę zmiennej w wyrażeniu dostępu do zmiennych. Już zostały wykonane praktyka Sprawdzanie typu węzła, a następnie rzutowania wyrażenia do dostępu do zmiennych, a następnie zaznaczając właściwości Typ określonego wyrażenia:

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

## <a name="creating-expression-trees"></a>Tworzenie drzewa wyrażeń

`System.Linq.Expression` Klasa zawiera także wiele metod statycznych do tworzenia wyrażenia. Te metody tworzenia węzła wyrażenia przy użyciu argumentów dla jego elementów podrzędnych. W ten sposób tworzenia wyrażenia z jego węzłów liści. Na przykład ten kod tworzy wyrażenie Dodaj:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Widać w tym prostym przykładzie, że wiele typów są zaangażowane w tworzenie i Praca z drzewa wyrażeń. Złożoność jest niezbędne do zapewnienia możliwości sformatowanego słownictwa podał języka C#.

## <a name="navigating-the-apis"></a>Nawigowanie po interfejsy API
Brak wyrażenia typy węzłów, które mapują prawie wszystkie elementy składni języka C#. Każdy typ ma określonej metody dla tego typu elementu języka. Istnieje wiele przechowywanych w nagłówek w tym samym czasie. Zamiast próby pamiętania wszystko, Oto techniki, używanych do pracy z drzewa wyrażeń:
1. Przyjrzyj się członków `ExpressionType` wyliczenia można określić możliwych węzłów, użytkownik powinien być badanie. Pomaga to naprawdę umożliwia przechodzenie między danymi i zrozumienie drzewo wyrażenia.
2. Przyjrzyj się statyczne elementy członkowskie `Expression` klasa do tworzenia wyrażenia. Tych metod można tworzyć dowolnego typu wyrażenia z zestawu jej podrzędnych węzłów.
3. Przyjrzyj się `ExpressionVisitor` klasa do tworzenia drzewa wyrażenia zmodyfikowane.

Można znaleźć więcej podczas wyszukiwania na każdym z tych trzech obszarach. Znajdziesz się niezmiennie, należy podczas uruchamiania jednego z tych trzech kroków.
 
 [Next — Wykonywanie drzew wyrażeń](expression-trees-execution.md)
 

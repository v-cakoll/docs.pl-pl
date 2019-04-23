---
title: Typy platform obsługujące drzewa wyrażeń
description: Informacje o typach framework obsługuje drzew wyrażeń, tworzenia drzew wyrażeń i technik do pracy z drzewa wyrażeń interfejsów API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: c18bbfb1273156a4b070d1f195d9e823256fde9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198468"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy platform obsługujące drzewa wyrażeń

[Poprzednie — Drzewa wyrażeń — objaśnienie](expression-trees-explained.md)

Istnieje duża lista klas w ramach platformy .NET Core, współpracujących z drzewa wyrażeń.
Można zobaczyć pełną listę w <xref:System.Linq.Expressions>.
Zamiast uruchamiania za pośrednictwem z pełną listą, Przyjrzyjmy się, jak zostały zaprojektowane klasy framework.

W projekcie języka wyrażenie jest treść kod, który oblicza i zwraca wartość. Wyrażenia może być bardzo prosta: wyrażenie stałe `1` zwraca stałej wartości 1. Może być bardziej skomplikowane: Wyrażenie `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` zwraca jeden certyfikat główny dla równaniu kwadratowym (w przypadku, gdy równanie ma rozwiązania).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Wszystko zaczyna się od System.Linq.Expression

Jest jeden komplikacje związane z pracy z drzew wyrażeń, różne rodzaje wyrażeń są prawidłowe w wielu miejscach w programach. Należy wziąć pod uwagę wyrażenia przypisania. Po prawej stronie przypisania może być wartością stałą, zmienną, metodę wyrażenie wywołania lub inne osoby. Elastyczność tego języka oznacza, że może wystąpić wiele typów innego wyrażenia w dowolnym miejscu węzłach drzewa podczas przechodzenia do drzewa wyrażenie. W związku z tym gdy typ bazowy wyrażenia można pracować, to najprostszy sposób pracy. Czasami potrzebny dowiedzieć się więcej.
Klasa bazowa wyrażenie zawiera `NodeType` właściwości w tym celu.
Zwraca `ExpressionType` czyli wyliczenie typy możliwe wyrażenia.
Jeśli znasz już typ węzła, można rzutować go do tego typu i wykonać konkretne akcje, wiedząc, typ węzła wyrażenia. Można wyszukiwania dla niektórych typów węzłów, a następnie pracować z określonymi właściwościami, tego rodzaju wyrażenia.

Na przykład ten kod będzie drukować nazwę zmiennej dla wyrażenia dostępu do zmiennej. Czy mogę wykonano praktyka Sprawdzanie typu węzła, a następnie rzutowania wyrażenia dostępu do zmiennej, a następnie zaznaczając właściwości typu określonego wyrażenia:

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

`System.Linq.Expression` Klasa zawiera także wiele metod statycznych, aby tworzyć wyrażenia. Te metody tworzenia węzła wyrażenie, przy użyciu argumenty podane dla jego elementów podrzędnych. W ten sposób możesz utworzyć wyrażenie z jego węzły liści. Na przykład ten kod tworzy Dodaj wyrażenie:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Możesz zobaczyć ten prosty przykład, że wiele typów są zaangażowane w tworzenie i Praca z drzewa wyrażeń. Czy złożoność jest zapewnienie możliwości sformatowanego słownictwa zawartym w języku C#.

## <a name="navigating-the-apis"></a>Przejdź do interfejsów API
Istnieją typy węzłów wyrażenie, które mapują na niemal wszystkie elementy składni języka C#. Każdy typ ma określonych metod dla tego typu elementu języka. To znacznie ułatwia głowę w tym samym czasie. Zamiast próbować pamiętania wszystko, Oto techniki, używanych do pracy z drzewa wyrażeń:
1. Przyjrzyj się członkowie `ExpressionType` wyliczenia, aby ustalić możliwe węzły, które powinny być testowania oprogramowania. Pomaga to tak naprawdę, gdy użytkownik chce przejść i zrozumieć drzewo wyrażenia.
2. Spójrz na statyczne elementy członkowskie `Expression` klasa do tworzenia wyrażenia. Tych metod można tworzyć dowolnego typu wyrażenia z zestawu jej podrzędnych węzłów.
3. Przyjrzyj się `ExpressionVisitor` klasa do tworzenia drzewa wyrażeń zmodyfikowane.

Można znaleźć więcej jak Przyjrzyj się każdej z tych trzech obszarów. Znajdziesz się niezmiennie, należy podczas uruchamiania przy użyciu jednego z tych trzech kroków.
 
 [Dalej — Wykonywanie drzew wyrażeń](expression-trees-execution.md)

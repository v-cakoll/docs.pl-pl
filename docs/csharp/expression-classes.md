---
title: Typy platform obsługujące drzewa wyrażeń
description: Dowiedz się więcej o typach struktury obsługujących drzewa wyrażeń, tworzeniu drzew wyrażeń i technikach pracy z interfejsami API drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146089"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy platform obsługujące drzewa wyrażeń

[Poprzedni -- Drzewa wyrażenia wyjaśnione](expression-trees-explained.md)

Istnieje duża lista klas w ramach .NET Core, które współpracują z drzewa wyrażeń.
Pełną listę można <xref:System.Linq.Expressions>zobaczyć na .
Zamiast uruchamiać pełną listę, zrozummy, jak zostały zaprojektowane klasy framework.

W projekcie języka wyrażenie jest treścią kodu, który oblicza i zwraca wartość. Wyrażenia mogą być bardzo proste: `1` wyrażenie stałe zwraca stałą wartość 1. Mogą być bardziej skomplikowane: `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` wyrażenie zwraca jeden katalog główny dla równania kwadratowego (w przypadku, gdy równanie ma rozwiązanie).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Wszystko zaczyna się od System.Linq.Expression

Jedną ze złożoności pracy z drzewami wyrażeń jest to, że wiele różnych rodzajów wyrażeń jest prawidłowych w wielu miejscach w programach. Należy wziąć pod uwagę wyrażenie przypisania. Prawa strona przypisania może być wartością stałą, zmienną, wyrażeniem wywołania metody lub innymi. Ta elastyczność języka oznacza, że można napotkać wiele różnych typów wyrażeń w dowolnym miejscu w węzłach drzewa podczas przechodzenia przez drzewo wyrażeń. W związku z tym, gdy można pracować z typem wyrażenia podstawowego, jest to najprostszy sposób pracy. Czasami jednak musisz wiedzieć więcej.
Klasa wyrażenia podstawowego `NodeType` zawiera właściwość w tym celu.
Zwraca, `ExpressionType` który jest wyliczenie możliwych typów wyrażeń.
Gdy znasz typ węzła, można rzutować go do tego typu i wykonywać określone akcje znając typ węzła wyrażenia. Można wyszukać niektóre typy węzłów, a następnie pracować z określonymi właściwościami tego rodzaju wyrażenia.

Na przykład ten kod spowoduje wydrukowanie nazwy zmiennej dla wyrażenia dostępu zmiennego. Postępowałem zgodnie z praktyką sprawdzania typu węzła, a następnie rzutowania do wyrażenia dostępu zmiennego, a następnie sprawdzania właściwości określonego typu wyrażenia:

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

Klasa `System.Linq.Expression` zawiera również wiele metod statycznych do tworzenia wyrażeń. Metody te tworzą węzeł wyrażenia przy użyciu argumentów dostarczonych dla jego podrzędnych. W ten sposób można utworzyć wyrażenie z jego węzłów liścia. Na przykład ten kod tworzy add wyrażenie:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

W tym prostym przykładzie można zobaczyć, że wiele typów są zaangażowane w tworzenie i pracy z drzewa wyrażeń. Ta złożoność jest niezbędna do zapewnienia możliwości bogatego słownictwa dostarczonego przez język C#.

## <a name="navigating-the-apis"></a>Nawigowanie po interfejsach API
Istnieją typy węzłów wyrażenia, które mapują do prawie wszystkich elementów składni języka C#. Każdy typ ma określone metody dla tego typu elementu języka. To dużo, aby utrzymać się w głowie w jednym czasie. Zamiast próbować zapamiętać wszystko, oto techniki, których używam do pracy z drzewami wyrażenia:

1. Spójrz na członków `ExpressionType` wyliczenia, aby określić możliwe węzły, które należy zbadać. To naprawdę pomaga, gdy chcesz przechodzenia i zrozumieć drzewo wyrażeń.
2. Spójrz na statycznych `Expression` elementów członkowskich klasy do tworzenia wyrażenia. Te metody można utworzyć dowolny typ wyrażenia z zestawu węzłów podrzędnych.
3. Spójrz na `ExpressionVisitor` klasę, aby utworzyć drzewo wyrażenia zmodyfikowane.

Znajdziesz więcej, gdy spojrzysz na każdy z tych trzech obszarów. Niezmiennie, znajdziesz to, czego potrzebujesz, gdy zaczniesz od jednego z tych trzech kroków.

 [Dalej - Wykonywanie drzew wyrażeń](expression-trees-execution.md)

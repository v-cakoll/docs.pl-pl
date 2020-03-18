---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Lear jak można użyć klas wyliczenia, zamiast wyliczenia, jako sposób na rozwiązanie niektórych ograniczeń tego ostatniego.
ms.date: 10/08/2018
ms.openlocfilehash: fb2cbcd744f29c70a86e6f3300721934192eb752
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847183"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Używanie klas wyliczania zamiast typów wyliczenia

[Wyliczenia](../../../csharp/language-reference/builtin-types/enum.md) (lub *typy wyliczenia* w skrócie) są cienką otoką języka wokół typu integralnego. Można ograniczyć ich użycie do podczas przechowywania jednej wartości z zamkniętego zestawu wartości. Klasyfikacja oparta na rozmiarach (małych, średnich, dużych) jest dobrym przykładem. Używanie wyliczeń do sterowania przepływem lub bardziej niezawodnych abstrakcji może być [zapachem kodu.](https://deviq.com/code-smells/) Ten typ użycia prowadzi do kruchego kodu z wielu instrukcji przepływu sterowania sprawdzanie wartości wyliczenia.

Zamiast tego można utworzyć klasy wyliczenia, które umożliwiają wszystkie funkcje sformatowane języka obiektowego.

Jednak nie jest to temat krytyczny i w wielu przypadkach, dla uproszczenia, nadal można używać regularnych [typów wyliczenia,](../../../csharp/language-reference/builtin-types/enum.md) jeśli jest to twoje preferencje. W każdym razie użycie klas wyliczenia jest bardziej związane z pojęciami związanymi z biznesem.

## <a name="implement-an-enumeration-base-class"></a>Implementowanie klasy podstawowej wyliczania

Mikrousługi zamawiania w eShopOnContainers zawiera przykładową implementację klasy podstawowej wyliczania, jak pokazano w poniższym przykładzie:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public |
                                         BindingFlags.Static |
                                         BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;

        if (otherValue == null)
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

Tej klasy można użyć jako typu w dowolnej jednostce `CardType` lub `Enumeration` obiekcie wartości, jak w przypadku następującej: klasy:

```csharp
public class CardType : Enumeration
{
    public static readonly CardType Amex = new CardType(1, "Amex");
    public static readonly CardType Visa = new CardType(2, "Visa");
    public static readonly CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Jimmy Bogard. Klasy wyliczania** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. Alternatywy wyliczenia w C #** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Klasa wyliczania podstawowego w eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Przykładowa klasa wyliczania w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis - Klasy, które pomagają w produkcji silnie wpisane inteligentniejsze wyliczenia w .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Poprzedni](implement-value-objects.md)
>[następny](domain-model-layer-validations.md)

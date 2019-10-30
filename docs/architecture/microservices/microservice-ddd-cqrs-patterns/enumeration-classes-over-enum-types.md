---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Wyczyść, w jaki sposób można używać klas wyliczenia, zamiast wyliczeniowych, w celu rozwiązania niektórych ograniczeń dotyczących tego ostatniego.
ms.date: 10/08/2018
ms.openlocfilehash: 255bccab0e1fe71e00c0d0b47c8af05f80cb760b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093861"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Użyj klas wyliczenia zamiast typów wyliczeniowych

[Wyliczenia](../../../csharp/language-reference/keywords/enum.md) (lub *typy wyliczeniowe* dla krótki) są otoką języka cienkiego wokół typu całkowitego. Możesz chcieć ograniczyć ich użycie do momentu przechowywania jednej wartości z zamkniętego zestawu wartości. Klasyfikacja oparta na rozmiarach (mały, średni, duży) jest dobrym przykładem. Korzystanie z wyliczeń dla przepływu sterowania lub bardziej niezawodnych abstrakcji może być [zapachem kodu](https://deviq.com/code-smells/). Ten typ użycia prowadzi do delikatnego kodu z wieloma instrukcjami przepływu sterowania, sprawdzając wartości wyliczenia.

Zamiast tego można tworzyć klasy wyliczenia, które umożliwiają wszystkie bogate funkcje języka zorientowanego na obiekt.

Nie jest to jednak krytyczne zagadnienie i w wielu przypadkach dla uproszczenia można nadal używać zwykłych [typów wyliczeniowych](../../../csharp/language-reference/keywords/enum.md) , jeśli jest to Twoje preferencje. Mimo to użycie klas wyliczenia jest bardziej powiązane z pojęciami związanymi z biznesem.

## <a name="implement-an-enumeration-base-class"></a>Zaimplementuj wyliczaną klasę bazową

Mikrousługa porządkowania w eShopOnContainers zapewnia przykładową implementację klasy bazowej wyliczenia, jak pokazano w następującym przykładzie:

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

Tej klasy można użyć jako typu w dowolnej jednostce lub obiekcie wartości, tak jak w przypadku następujących `CardType`: `Enumeration` Class:

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wyliczenia to akcja — aktualizacja** \
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- **Daniel. Jak są rozłożone choroby i jak można ją wyznaczyć** \
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- **Jimmy Bogard. Klasy wyliczeniowe** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. Warianty wyliczenia C# w** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Podstawowa klasa wyliczenia w eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Przykładowa Klasa wyliczenia w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis-klasy, które ułatwiają tworzenie inteligentnych typów wyliczeniowych w programie .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Poprzedni](implement-value-objects.md)
>[Następny](domain-model-layer-validations.md)

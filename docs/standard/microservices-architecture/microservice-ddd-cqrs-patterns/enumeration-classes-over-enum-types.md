---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Wyczyść wykorzystania klas wyliczeń zamiast typów wyliczeniowych, jako sposób, aby rozwiązać niektóre ograniczenia.
ms.date: 10/08/2018
ms.openlocfilehash: 10b4c2f7b9f079ed535111e65b8154791f6575cd
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003839"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Użyj klas wyliczeń zamiast typów wyliczeń

[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (lub *typach wyliczeniowych* w skrócie) są alokowania elastycznego języka otokę typu całkowitego. Możesz chcieć ograniczyć ich wykorzystania, podczas przechowujesz jedną wartość z zamkniętej zestaw wartości. Klasyfikacja na podstawie rozmiarów (mały, Średni, duży) jest dobrym przykładem. Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodne abstrakcje może być [kodu zapachu](https://deviq.com/code-smells/). Tego rodzaju użycia prowadzi do wrażliwych kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.

Zamiast tego można utworzyć klasy wyliczenie, które umożliwiają bogatych funkcji obiektowy język.

Jednak nie jest to temat krytycznych i w wielu przypadkach dla uproszczenia można nadal używać zwykłe [typach wyliczeniowych](../../../csharp/language-reference/keywords/enum.md) przypadku swoje preferencje. Mimo to używanie klas wyliczeń są bardziej powiązane ze pojęć związanych z firmą.

## <a name="implement-an-enumeration-base-class"></a>Implementowanie klasy bazowej wyliczenia

Szeregowania mikrousługi w ramach aplikacji eShopOnContainers zawiera przykład implementacji klasy podstawowej wyliczenie, jak pokazano w poniższym przykładzie:

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

Ta klasa służy jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następujących `CardType` : `Enumeration` klasy:

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

- **Wyliczenia są Akcja — aktualizacja** \
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- **Daniel Hardman. Jak typy wyliczeniowe rozprzestrzeniają się choroby — Oraz w celu usunięcia go** \
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- **Jimmy Bogard. Wyliczanie klas** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. Alternatywy wyliczenia w języku C#** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Podstawowa klasa wyliczeniowa w ramach aplikacji eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Przykładowa klasa wyliczenia w ramach aplikacji eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- **SmartEnum**. Ardalis - klasy, aby utworzyć silnie typizowane wyliczenia inteligentniejsze na platformie .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Poprzednie](implement-value-objects.md)
>[dalej](domain-model-layer-validations.md)

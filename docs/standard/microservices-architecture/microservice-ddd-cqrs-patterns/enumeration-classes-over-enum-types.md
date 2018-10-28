---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Używanie klas wyliczeń zamiast typów wyliczeń
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 60d8c8e88cca19c92f6a1364bf2fbbf0500081c3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195726"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Używanie klas wyliczeń zamiast typów wyliczeń

[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (lub *typach wyliczeniowych* w skrócie) są alokowania elastycznego języka otokę typu całkowitego. Możesz chcieć ograniczyć ich wykorzystania, podczas przechowujesz jedną wartość z zamkniętej zestaw wartości. Klasyfikacja na podstawie rozmiarów (mały, Średni, duży) jest dobrym przykładem. Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodne abstrakcje może być [kodu zapachu](https://deviq.com/code-smells/). Tego rodzaju użycia prowadzi do wrażliwych kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.

Zamiast tego można utworzyć klasy wyliczenie, które umożliwiają bogatych funkcji obiektowy język.

Jednak nie jest to temat krytycznych i w wielu przypadkach dla uproszczenia można nadal używać zwykłe [typach wyliczeniowych](../../../../docs/csharp/language-reference/keywords/enum.md) przypadku swoje preferencje.

## <a name="implementing-an-enumeration-base-class"></a>Implementacja klasy bazowej wyliczenia

Szeregowania mikrousługi w ramach aplikacji eShopOnContainers zawiera przykład implementacji klasy podstawowej wyliczenie, jak pokazano w poniższym przykładzie:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }
    
    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | BindingFlags.Static | BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

Klasa jest używana jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następującej klasy wyliczenie CardType:

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    {
    }

    private class AmexCardType : CardType
    {
        public AmexCardType(): base(1, "Amex")
        { }
    }
    
    private class VisaCardType : CardType
    {
        public VisaCardType(): base(2, "Visa")
        { }
    }
    
    private class MasterCardType : CardType
    {
        public MasterCardType(): base(3, "MasterCard")
        { }
    }
}
```

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wyliczenia są Akcja — aktualizacja**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Daniel Hardman. Jak typy wyliczeniowe rozprzestrzeniają się choroby — Oraz w celu usunięcia go**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Wyliczanie klas**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Alternatywy wyliczenia w języku C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Klasa bazowa wyliczenia w ramach aplikacji eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Przykładowa klasa wyliczenia w ramach aplikacji eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Poprzednie](implement-value-objects.md)
[dalej](domain-model-layer-validations.md)

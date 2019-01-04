---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Wyczyść wykorzystania klas wyliczeń zamiast typów wyliczeniowych, jako sposób, aby rozwiązać niektóre ograniczenia.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 72a3e7ef8043e0016cefb45a4182b5c2e3061753
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029713"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Użyj klas wyliczeń zamiast typów wyliczeń

[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (lub *typach wyliczeniowych* w skrócie) są alokowania elastycznego języka otokę typu całkowitego. Możesz chcieć ograniczyć ich wykorzystania, podczas przechowujesz jedną wartość z zamkniętej zestaw wartości. Klasyfikacja na podstawie rozmiarów (mały, Średni, duży) jest dobrym przykładem. Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodne abstrakcje może być [kodu zapachu](http://deviq.com/code-smells/). Tego rodzaju użycia prowadzi do wrażliwych kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.

Zamiast tego można utworzyć klasy wyliczenie, które umożliwiają bogatych funkcji obiektowy język.

Jednak nie jest to temat krytycznych i w wielu przypadkach dla uproszczenia można nadal używać zwykłe [typach wyliczeniowych](../../../csharp/language-reference/keywords/enum.md) przypadku swoje preferencje. Mimo to używanie klas wyliczeń są bardziej powiązane ze pojęć związanych z firmą.

## <a name="implement-an-enumeration-base-class"></a>Implementowanie klasy bazowej wyliczenia

Szeregowania mikrousługi w ramach aplikacji eShopOnContainers zawiera przykład implementacji klasy podstawowej wyliczenie, jak pokazano w poniższym przykładzie:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration()
    { }

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
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    { }

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

- **Wyliczenia są Akcja — aktualizacja** \
  [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

- **Daniel Hardman. Jak typy wyliczeniowe rozprzestrzeniają się choroby — Oraz w celu usunięcia go** \
  [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

- **Jimmy Bogard. Wyliczanie klas** \
  [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

- **Steve Smith. Alternatywy wyliczenia w języku C#** \
  [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

- **Enumeration.cs.** Podstawowa klasa wyliczeniowa w ramach aplikacji eShopOnContainers \
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

- **CardType.cs**. Przykładowa klasa wyliczenia w ramach aplikacji eShopOnContainers. \
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)
    
- **SmartEnum**. Ardalis - klasy, aby utworzyć silnie typizowane wyliczenia inteligentniejsze na platformie .NET. \
  [*https://www.nuget.org/packages/Ardalis.SmartEnum/*](https://www.nuget.org/packages/Ardalis.SmartEnum/)

>[!div class="step-by-step"]
>[Poprzednie](implement-value-objects.md)
>[dalej](domain-model-layer-validations.md)
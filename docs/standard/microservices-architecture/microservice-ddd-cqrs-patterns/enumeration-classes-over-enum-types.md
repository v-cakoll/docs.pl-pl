---
title: "Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 88decdc2f2ea945dc04cdb66402b12bd972414ce
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe

[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (*wyliczenia* skrócie) są alokowania języka otokę typ całkowity. Możesz chcieć ograniczyć ich wykorzystania, gdy jedna wartość z zamkniętego zestawu wartości są przechowywane. Klasyfikacja na podstawie płci (na przykład męskiego, gniazdo, nieznany) lub rozmiary (S-M, L, XL) są dobre przykłady. Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodna abstrakcje może być [kodu zapachu](http://deviq.com/code-smells/). Ten typ użycia doprowadzi do słabe kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.

Zamiast tego można utworzyć klasy wyliczenia, które umożliwiają rozbudowane funkcje zorientowany obiektowo język. Jednak nie jest to problem krytyczny i w wielu przypadkach, dla uproszczenia, można nadal używać regularne wyliczenia czyli swoich preferencji.

## <a name="implementing-enumeration-classes"></a>Implementowanie klas — wyliczenie

Porządkowania mikrousługi w eShopOnContainers zawiera przykładowe zastosowanie klasy podstawowej wyliczenia, jak pokazano w poniższym przykładzie:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

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

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
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

Ta klasa służy jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następującej klasy CardType wyliczenia.

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }


    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Enum jest akcja — aktualizacja**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Hardman Danielowi. Jak wyliczenia rozprzestrzeniają się choroby — Oraz sposób jego utwardzanie**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Wyliczanie klas**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Wyliczenia alternatyw w języku C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Podstawowa klasa w eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Przykładowe klasy wyliczenie w eShopOnContainers.
    [*https://github.com/DotNet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.domain/AggregatesModel/BuyerAggregate/CardType.CS*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Poprzednie] (wdrożenie — wartość objects.md) [dalej] (domena — model warstwy validations.md)

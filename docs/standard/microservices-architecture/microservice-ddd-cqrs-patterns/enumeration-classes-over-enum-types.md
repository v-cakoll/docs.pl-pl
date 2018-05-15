---
title: Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 1cb8c6115602d80b61f1116cbb1a8df4fbcee028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="39e0d-103">Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="39e0d-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="39e0d-104">[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (lub *Typy wyliczeniowe* skrócie) są alokowania języka otokę typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="39e0d-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="39e0d-105">Możesz chcieć ograniczyć ich wykorzystania, gdy jedna wartość z zamkniętego zestawu wartości są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="39e0d-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="39e0d-106">Klasyfikacja na podstawie płci (na przykład męskiego, gniazdo, nieznany) lub rozmiarów (małe, średnie, duża) są dobre przykłady.</span><span class="sxs-lookup"><span data-stu-id="39e0d-106">Classification based on gender (for example, male, female, unknown) or sizes (small, medium, large) are good examples.</span></span> <span data-ttu-id="39e0d-107">Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodna abstrakcje może być [kodu zapachu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="39e0d-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="39e0d-108">Ten typ użycia prowadzi do słabe kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="39e0d-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="39e0d-109">Zamiast tego można utworzyć klasy wyliczenia, które umożliwiają rozbudowane funkcje zorientowany obiektowo język.</span><span class="sxs-lookup"><span data-stu-id="39e0d-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="39e0d-110">Jednak nie jest to temat krytycznych i w wielu przypadkach, dla uproszczenia, można nadal używać regular [Typy wyliczeniowe](../../../../docs/csharp/language-reference/keywords/enum.md) przypadku swoich preferencji.</span><span class="sxs-lookup"><span data-stu-id="39e0d-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="39e0d-111">Implementacja klasy podstawowej — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="39e0d-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="39e0d-112">Porządkowania mikrousługi w eShopOnContainers zawiera przykładowe zastosowanie klasy podstawowej wyliczenia, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39e0d-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="39e0d-113">Ta klasa służy jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następującej klasy wyliczenie CardType:</span><span class="sxs-lookup"><span data-stu-id="39e0d-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="39e0d-114">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="39e0d-114">Additional resources</span></span>

-   <span data-ttu-id="39e0d-115">**Enum jest akcja — aktualizacja**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="39e0d-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="39e0d-116">**Hardman Danielowi. Jak wyliczenia rozprzestrzeniają się choroby — Oraz sposób jego Utwardzanie**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="39e0d-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="39e0d-117">**Jimmy Bogard. Wyliczanie klas**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="39e0d-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="39e0d-118">**Steve Smith. Wyliczenia alternatyw w języku C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="39e0d-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="39e0d-119">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="39e0d-119">**Enumeration.cs.**</span></span> <span data-ttu-id="39e0d-120">Klasa podstawowa wyliczenia w eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="39e0d-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="39e0d-121">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="39e0d-121">**CardType.cs**.</span></span> <span data-ttu-id="39e0d-122">Przykładowe klasy wyliczenie w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="39e0d-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="39e0d-123">[Poprzednie] (wdrożenie — wartość objects.md) [dalej] (domena — model warstwy validations.md)</span><span class="sxs-lookup"><span data-stu-id="39e0d-123">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>

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
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="69e32-104">Za pomocą klasy wyliczenie zamiast Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="69e32-104">Using Enumeration classes instead of enum types</span></span>

<span data-ttu-id="69e32-105">[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (*wyliczenia* skrócie) są alokowania języka otokę typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="69e32-105">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (*enums* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="69e32-106">Możesz chcieć ograniczyć ich wykorzystania, gdy jedna wartość z zamkniętego zestawu wartości są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="69e32-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="69e32-107">Klasyfikacja na podstawie płci (na przykład męskiego, gniazdo, nieznany) lub rozmiary (S-M, L, XL) są dobre przykłady.</span><span class="sxs-lookup"><span data-stu-id="69e32-107">Classification based on gender (for example, male, female, unknown), or sizes (S, M, L, XL) are good examples.</span></span> <span data-ttu-id="69e32-108">Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodna abstrakcje może być [kodu zapachu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="69e32-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="69e32-109">Ten typ użycia doprowadzi do słabe kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="69e32-109">This type of usage will lead to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="69e32-110">Zamiast tego można utworzyć klasy wyliczenia, które umożliwiają rozbudowane funkcje zorientowany obiektowo język.</span><span class="sxs-lookup"><span data-stu-id="69e32-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span> <span data-ttu-id="69e32-111">Jednak nie jest to problem krytyczny i w wielu przypadkach, dla uproszczenia, można nadal używać regularne wyliczenia czyli swoich preferencji.</span><span class="sxs-lookup"><span data-stu-id="69e32-111">However, this is not a critical issue and in many cases, for simplicity, you can still use regular enums if that is your preference.</span></span>

## <a name="implementing-enumeration-classes"></a><span data-ttu-id="69e32-112">Implementowanie klas — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="69e32-112">Implementing Enumeration classes</span></span>

<span data-ttu-id="69e32-113">Porządkowania mikrousługi w eShopOnContainers zawiera przykładowe zastosowanie klasy podstawowej wyliczenia, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="69e32-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="69e32-114">Ta klasa służy jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następującej klasy CardType wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="69e32-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="69e32-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="69e32-115">Additional resources</span></span>

-   <span data-ttu-id="69e32-116">**Enum jest akcja — aktualizacja**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="69e32-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="69e32-117">**Hardman Danielowi. Jak wyliczenia rozprzestrzeniają się choroby — Oraz sposób jego utwardzanie**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="69e32-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="69e32-118">**Jimmy Bogard. Wyliczanie klas**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="69e32-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="69e32-119">**Steve Smith. Wyliczenia alternatyw w języku C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="69e32-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="69e32-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="69e32-120">**Enumeration.cs.**</span></span> <span data-ttu-id="69e32-121">Podstawowa klasa w eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="69e32-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="69e32-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="69e32-122">**CardType.cs**.</span></span> <span data-ttu-id="69e32-123">Przykładowe klasy wyliczenie w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="69e32-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="69e32-124">*https://github.com/DotNet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.domain/AggregatesModel/BuyerAggregate/CardType.CS*</span><span class="sxs-lookup"><span data-stu-id="69e32-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="69e32-125">[Poprzednie] (wdrożenie — wartość objects.md) [dalej] (domena — model warstwy validations.md)</span><span class="sxs-lookup"><span data-stu-id="69e32-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>

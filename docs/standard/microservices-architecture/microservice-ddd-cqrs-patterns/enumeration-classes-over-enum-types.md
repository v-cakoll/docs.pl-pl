---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Używanie klas wyliczeń zamiast typów wyliczeń
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: f1b88d160d6532c2a768684b55cd236417699322
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723532"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="25fe2-103">Używanie klas wyliczeń zamiast typów wyliczeń</span><span class="sxs-lookup"><span data-stu-id="25fe2-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="25fe2-104">[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (lub *typach wyliczeniowych* w skrócie) są alokowania elastycznego języka otokę typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="25fe2-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="25fe2-105">Możesz chcieć ograniczyć ich wykorzystania, podczas przechowujesz jedną wartość z zamkniętej zestaw wartości.</span><span class="sxs-lookup"><span data-stu-id="25fe2-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="25fe2-106">Klasyfikacja na podstawie rozmiarów (mały, Średni, duży) jest dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="25fe2-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="25fe2-107">Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodne abstrakcje może być [kodu zapachu](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="25fe2-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="25fe2-108">Tego rodzaju użycia prowadzi do wrażliwych kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="25fe2-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="25fe2-109">Zamiast tego można utworzyć klasy wyliczenie, które umożliwiają bogatych funkcji obiektowy język.</span><span class="sxs-lookup"><span data-stu-id="25fe2-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="25fe2-110">Jednak nie jest to temat krytycznych i w wielu przypadkach dla uproszczenia można nadal używać zwykłe [typach wyliczeniowych](../../../../docs/csharp/language-reference/keywords/enum.md) przypadku swoje preferencje.</span><span class="sxs-lookup"><span data-stu-id="25fe2-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="25fe2-111">Implementacja klasy bazowej wyliczenia</span><span class="sxs-lookup"><span data-stu-id="25fe2-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="25fe2-112">Szeregowania mikrousługi w ramach aplikacji eShopOnContainers zawiera przykład implementacji klasy podstawowej wyliczenie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="25fe2-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="25fe2-113">Klasa jest używana jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następującej klasy wyliczenie CardType:</span><span class="sxs-lookup"><span data-stu-id="25fe2-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="25fe2-114">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="25fe2-114">Additional resources</span></span>

-   <span data-ttu-id="25fe2-115">**Wyliczenia są Akcja — aktualizacja**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="25fe2-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="25fe2-116">**Daniel Hardman. Jak typy wyliczeniowe rozprzestrzeniają się choroby — Oraz w celu usunięcia go**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="25fe2-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="25fe2-117">**Jimmy Bogard. Wyliczanie klas**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="25fe2-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="25fe2-118">**Steve Smith. Alternatywy wyliczenia w języku C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="25fe2-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="25fe2-119">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="25fe2-119">**Enumeration.cs.**</span></span> <span data-ttu-id="25fe2-120">Klasa bazowa wyliczenia w ramach aplikacji eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="25fe2-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="25fe2-121">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="25fe2-121">**CardType.cs**.</span></span> <span data-ttu-id="25fe2-122">Przykładowa klasa wyliczenia w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="25fe2-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="25fe2-123">[Poprzednie](implement-value-objects.md)
[dalej](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="25fe2-123">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>

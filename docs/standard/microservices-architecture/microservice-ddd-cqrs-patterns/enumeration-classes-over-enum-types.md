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
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="ebf8f-103">Użyj klas wyliczeń zamiast typów wyliczeń</span><span class="sxs-lookup"><span data-stu-id="ebf8f-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="ebf8f-104">[Wyliczenia](../../../../docs/csharp/language-reference/keywords/enum.md) (lub *typach wyliczeniowych* w skrócie) są alokowania elastycznego języka otokę typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="ebf8f-105">Możesz chcieć ograniczyć ich wykorzystania, podczas przechowujesz jedną wartość z zamkniętej zestaw wartości.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="ebf8f-106">Klasyfikacja na podstawie rozmiarów (mały, Średni, duży) jest dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="ebf8f-107">Przy użyciu wyliczenia przepływu sterowania i bardziej niezawodne abstrakcje może być [kodu zapachu](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="ebf8f-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="ebf8f-108">Tego rodzaju użycia prowadzi do wrażliwych kodu o wielu instrukcjach przepływu sterowania sprawdzanie wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="ebf8f-109">Zamiast tego można utworzyć klasy wyliczenie, które umożliwiają bogatych funkcji obiektowy język.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="ebf8f-110">Jednak nie jest to temat krytycznych i w wielu przypadkach dla uproszczenia można nadal używać zwykłe [typach wyliczeniowych](../../../csharp/language-reference/keywords/enum.md) przypadku swoje preferencje.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/keywords/enum.md) if that's your preference.</span></span> <span data-ttu-id="ebf8f-111">Mimo to używanie klas wyliczeń są bardziej powiązane ze pojęć związanych z firmą.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="ebf8f-112">Implementowanie klasy bazowej wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ebf8f-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="ebf8f-113">Szeregowania mikrousługi w ramach aplikacji eShopOnContainers zawiera przykład implementacji klasy podstawowej wyliczenie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ebf8f-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="ebf8f-114">Ta klasa służy jako typ w dowolnym obiekcie jednostka lub wartość, jak w przypadku następujących `CardType` : `Enumeration` klasy:</span><span class="sxs-lookup"><span data-stu-id="ebf8f-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="ebf8f-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="ebf8f-115">Additional resources</span></span>

- <span data-ttu-id="ebf8f-116">**Wyliczenia są Akcja — aktualizacja** \\</span><span class="sxs-lookup"><span data-stu-id="ebf8f-116">**Enum’s are evil—update** \\</span></span>
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="ebf8f-117">**Daniel Hardman. Jak typy wyliczeniowe rozprzestrzeniają się choroby — Oraz w celu usunięcia go** \\</span><span class="sxs-lookup"><span data-stu-id="ebf8f-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** \\</span></span>
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="ebf8f-118">**Jimmy Bogard. Wyliczanie klas** \\</span><span class="sxs-lookup"><span data-stu-id="ebf8f-118">**Jimmy Bogard. Enumeration classes** \\</span></span>
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="ebf8f-119">**Steve Smith. Alternatywy wyliczenia w języku C#** \\</span><span class="sxs-lookup"><span data-stu-id="ebf8f-119">**Steve Smith. Enum Alternatives in C#** \\</span></span>
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="ebf8f-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="ebf8f-120">**Enumeration.cs.**</span></span> <span data-ttu-id="ebf8f-121">Podstawowa klasa wyliczeniowa w ramach aplikacji eShopOnContainers \\</span><span class="sxs-lookup"><span data-stu-id="ebf8f-121">Base Enumeration class in eShopOnContainers \\</span></span>
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="ebf8f-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-122">**CardType.cs**.</span></span> <span data-ttu-id="ebf8f-123">Przykładowa klasa wyliczenia w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- <span data-ttu-id="ebf8f-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-124">**SmartEnum**.</span></span> <span data-ttu-id="ebf8f-125">Ardalis - klasy, aby utworzyć silnie typizowane wyliczenia inteligentniejsze na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="ebf8f-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="ebf8f-126">[Poprzednie](implement-value-objects.md)
>[dalej](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="ebf8f-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>

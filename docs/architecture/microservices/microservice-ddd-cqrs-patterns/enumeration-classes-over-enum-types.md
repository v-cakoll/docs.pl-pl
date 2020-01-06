---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Wyczyść, w jaki sposób można używać klas wyliczenia, zamiast wyliczeniowych, w celu rozwiązania niektórych ograniczeń dotyczących tego ostatniego.
ms.date: 10/08/2018
ms.openlocfilehash: 6752adb28b1bd0982c66fa2d021b04b999447c6e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337680"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="f7faf-103">Użyj klas wyliczenia zamiast typów wyliczeniowych</span><span class="sxs-lookup"><span data-stu-id="f7faf-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="f7faf-104">[Wyliczenia](../../../csharp/language-reference/builtin-types/enum.md) (lub *typy wyliczeniowe* dla krótki) są otoką języka cienkiego wokół typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="f7faf-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="f7faf-105">Możesz chcieć ograniczyć ich użycie do momentu przechowywania jednej wartości z zamkniętego zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="f7faf-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="f7faf-106">Klasyfikacja oparta na rozmiarach (mały, średni, duży) jest dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="f7faf-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="f7faf-107">Korzystanie z wyliczeń dla przepływu sterowania lub bardziej niezawodnych abstrakcji może być [zapachem kodu](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="f7faf-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="f7faf-108">Ten typ użycia prowadzi do delikatnego kodu z wieloma instrukcjami przepływu sterowania, sprawdzając wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f7faf-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="f7faf-109">Zamiast tego można tworzyć klasy wyliczenia, które umożliwiają wszystkie bogate funkcje języka zorientowanego na obiekt.</span><span class="sxs-lookup"><span data-stu-id="f7faf-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="f7faf-110">Nie jest to jednak krytyczne zagadnienie i w wielu przypadkach dla uproszczenia można nadal używać zwykłych [typów wyliczeniowych](../../../csharp/language-reference/builtin-types/enum.md) , jeśli jest to Twoje preferencje.</span><span class="sxs-lookup"><span data-stu-id="f7faf-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="f7faf-111">Mimo to użycie klas wyliczenia jest bardziej powiązane z pojęciami związanymi z biznesem.</span><span class="sxs-lookup"><span data-stu-id="f7faf-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="f7faf-112">Zaimplementuj wyliczaną klasę bazową</span><span class="sxs-lookup"><span data-stu-id="f7faf-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="f7faf-113">Mikrousługa porządkowania w eShopOnContainers zapewnia przykładową implementację klasy bazowej wyliczenia, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f7faf-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="f7faf-114">Tej klasy można użyć jako typu w dowolnej jednostce lub obiekcie wartości, tak jak w przypadku następujących `CardType`: `Enumeration` Class:</span><span class="sxs-lookup"><span data-stu-id="f7faf-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="f7faf-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f7faf-115">Additional resources</span></span>

- <span data-ttu-id="f7faf-116">**Wyliczenia to akcja — aktualizacja** </span><span class="sxs-lookup"><span data-stu-id="f7faf-116">**Enum’s are evil—update** </span></span>\
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="f7faf-117">**Daniel. Jak są rozłożone choroby i jak można ją wyznaczyć** </span><span class="sxs-lookup"><span data-stu-id="f7faf-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** </span></span>\
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="f7faf-118">**Jimmy Bogard. Klasy wyliczeniowe** </span><span class="sxs-lookup"><span data-stu-id="f7faf-118">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="f7faf-119">**Steve Smith. Warianty wyliczenia C# w** </span><span class="sxs-lookup"><span data-stu-id="f7faf-119">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="f7faf-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="f7faf-120">**Enumeration.cs.**</span></span> <span data-ttu-id="f7faf-121">Podstawowa klasa wyliczenia w eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="f7faf-121">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="f7faf-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="f7faf-122">**CardType.cs**.</span></span> <span data-ttu-id="f7faf-123">Przykładowa Klasa wyliczenia w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f7faf-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="f7faf-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="f7faf-124">**SmartEnum**.</span></span> <span data-ttu-id="f7faf-125">Ardalis-klasy, które ułatwiają tworzenie inteligentnych typów wyliczeniowych w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="f7faf-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="f7faf-126">[Poprzedni](implement-value-objects.md)
>[Następny](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="f7faf-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>

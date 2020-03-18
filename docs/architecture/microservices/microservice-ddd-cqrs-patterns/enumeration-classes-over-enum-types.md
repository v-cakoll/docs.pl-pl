---
title: Używanie klas wyliczeń zamiast typów wyliczeń
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Lear jak można użyć klas wyliczenia, zamiast wyliczenia, jako sposób na rozwiązanie niektórych ograniczeń tego ostatniego.
ms.date: 10/08/2018
ms.openlocfilehash: fb2cbcd744f29c70a86e6f3300721934192eb752
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847183"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="b1997-103">Używanie klas wyliczania zamiast typów wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b1997-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="b1997-104">[Wyliczenia](../../../csharp/language-reference/builtin-types/enum.md) (lub *typy wyliczenia* w skrócie) są cienką otoką języka wokół typu integralnego.</span><span class="sxs-lookup"><span data-stu-id="b1997-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="b1997-105">Można ograniczyć ich użycie do podczas przechowywania jednej wartości z zamkniętego zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="b1997-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="b1997-106">Klasyfikacja oparta na rozmiarach (małych, średnich, dużych) jest dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="b1997-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="b1997-107">Używanie wyliczeń do sterowania przepływem lub bardziej niezawodnych abstrakcji może być [zapachem kodu.](https://deviq.com/code-smells/)</span><span class="sxs-lookup"><span data-stu-id="b1997-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="b1997-108">Ten typ użycia prowadzi do kruchego kodu z wielu instrukcji przepływu sterowania sprawdzanie wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b1997-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="b1997-109">Zamiast tego można utworzyć klasy wyliczenia, które umożliwiają wszystkie funkcje sformatowane języka obiektowego.</span><span class="sxs-lookup"><span data-stu-id="b1997-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="b1997-110">Jednak nie jest to temat krytyczny i w wielu przypadkach, dla uproszczenia, nadal można używać regularnych [typów wyliczenia,](../../../csharp/language-reference/builtin-types/enum.md) jeśli jest to twoje preferencje.</span><span class="sxs-lookup"><span data-stu-id="b1997-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="b1997-111">W każdym razie użycie klas wyliczenia jest bardziej związane z pojęciami związanymi z biznesem.</span><span class="sxs-lookup"><span data-stu-id="b1997-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="b1997-112">Implementowanie klasy podstawowej wyliczania</span><span class="sxs-lookup"><span data-stu-id="b1997-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="b1997-113">Mikrousługi zamawiania w eShopOnContainers zawiera przykładową implementację klasy podstawowej wyliczania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b1997-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="b1997-114">Tej klasy można użyć jako typu w dowolnej jednostce `CardType` lub `Enumeration` obiekcie wartości, jak w przypadku następującej: klasy:</span><span class="sxs-lookup"><span data-stu-id="b1997-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static readonly CardType Amex = new CardType(1, "Amex");
    public static readonly CardType Visa = new CardType(2, "Visa");
    public static readonly CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="b1997-115">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="b1997-115">Additional resources</span></span>

- <span data-ttu-id="b1997-116">**Jimmy Bogard. Klasy wyliczania** </span><span class="sxs-lookup"><span data-stu-id="b1997-116">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="b1997-117">**Steve Smith. Alternatywy wyliczenia w C #** </span><span class="sxs-lookup"><span data-stu-id="b1997-117">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="b1997-118">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="b1997-118">**Enumeration.cs.**</span></span> <span data-ttu-id="b1997-119">Klasa wyliczania podstawowego w eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="b1997-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="b1997-120">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="b1997-120">**CardType.cs**.</span></span> <span data-ttu-id="b1997-121">Przykładowa klasa wyliczania w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b1997-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="b1997-122">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="b1997-122">**SmartEnum**.</span></span> <span data-ttu-id="b1997-123">Ardalis - Klasy, które pomagają w produkcji silnie wpisane inteligentniejsze wyliczenia w .NET.</span><span class="sxs-lookup"><span data-stu-id="b1997-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="b1997-124">[Poprzedni](implement-value-objects.md)
>[następny](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="b1997-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>

---
title: Typy — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709026"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="675c2-102">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="675c2-102">Type Design Guidelines</span></span>
<span data-ttu-id="675c2-103">Z perspektywy środowiska CLR istnieją tylko dwie kategorie typów — typy referencyjne i typy wartości — ale na potrzeby dyskusji na temat projektu struktury dzielą typy na więcej grup logicznych, z których każda ma własne specyficzne reguły projektowania.</span><span class="sxs-lookup"><span data-stu-id="675c2-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="675c2-104">Klasy są ogólną wielkością liter typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="675c2-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="675c2-105">Składają się na siebie zbiory typów w większości platform.</span><span class="sxs-lookup"><span data-stu-id="675c2-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="675c2-106">Klasy są długoterminowe w rozbudowanym zestawie funkcji opartych na obiektach, które obsługują i do ich ogólnego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="675c2-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="675c2-107">Klasy bazowe i klasy abstrakcyjne są specjalnymi grupami logicznymi związanymi z rozszerzalnością.</span><span class="sxs-lookup"><span data-stu-id="675c2-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="675c2-108">Interfejsy to typy, które mogą być implementowane przez oba typy odwołań i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="675c2-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="675c2-109">Mogą to być jako elementy główne hierarchii polimorficznych typów referencyjnych i typów wartości.</span><span class="sxs-lookup"><span data-stu-id="675c2-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="675c2-110">Ponadto interfejsy mogą służyć do symulowania wielokrotnego dziedziczenia, które nie jest natywnie obsługiwane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="675c2-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="675c2-111">Struktury są ogólną wielkością liter typów wartości i powinny być zarezerwowane dla małych, prostych typów, podobnie jak w przypadku elementów podstawowych języka.</span><span class="sxs-lookup"><span data-stu-id="675c2-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="675c2-112">Wyliczenia są szczególnym przypadkiem typów wartości używanych do definiowania krótkich zestawów wartości, takich jak dni tygodnia, kolory konsoli i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="675c2-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="675c2-113">Klasy statyczne są typami przeznaczonymi do kontenerów dla statycznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="675c2-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="675c2-114">Są one często używane do udostępniania skrótów do innych operacji.</span><span class="sxs-lookup"><span data-stu-id="675c2-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="675c2-115">Delegaty, wyjątki, atrybuty, tablice i kolekcje są szczególnymi przypadkami typów referencyjnych, które są przeznaczone do określonych zastosowań, oraz wskazówki dotyczące ich projektowania i użycia zostały omówione w innym miejscu w tej książce.</span><span class="sxs-lookup"><span data-stu-id="675c2-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="675c2-116">**✓ DO** upewnij się, że każdy typ jest dobrze zdefiniowany zestaw elementów członkowskich powiązane, nie tylko losowe kolekcji funkcji niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="675c2-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="675c2-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="675c2-117">In This Section</span></span>  
 [<span data-ttu-id="675c2-118">Wybieranie między klasą i strukturą</span><span class="sxs-lookup"><span data-stu-id="675c2-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="675c2-119">Projekt klasy abstrakcyjnej</span><span class="sxs-lookup"><span data-stu-id="675c2-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="675c2-120">Projekt klasy statycznej</span><span class="sxs-lookup"><span data-stu-id="675c2-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="675c2-121">Projekt interfejsu</span><span class="sxs-lookup"><span data-stu-id="675c2-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="675c2-122">Projekt struktury</span><span class="sxs-lookup"><span data-stu-id="675c2-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="675c2-123">Projekt wyliczeń</span><span class="sxs-lookup"><span data-stu-id="675c2-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="675c2-124">Zagnieżdżone typy</span><span class="sxs-lookup"><span data-stu-id="675c2-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="675c2-125">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="675c2-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="675c2-126">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="675c2-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675c2-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="675c2-127">See also</span></span>

- [<span data-ttu-id="675c2-128">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="675c2-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

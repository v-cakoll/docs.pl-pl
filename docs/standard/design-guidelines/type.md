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
author: KrzysztofCwalina
ms.openlocfilehash: 16f2a095f461a406eedbd2b34b0c91d3ac43bbe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650105"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="fb1e8-102">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="fb1e8-102">Type Design Guidelines</span></span>
<span data-ttu-id="fb1e8-103">Z perspektywy CLR są tylko dwie kategorie typów — typy referencyjne i typy wartości — ale na potrzeby dyskusji na temat projektowania framework, możemy podzielić typy bardziej logiczne, grup, każda z regułach określonego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="fb1e8-104">Klasy są generalnie w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="fb1e8-105">Stanowią one większość typów w większości środowisk.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="fb1e8-106">Klasy zobowiązań ich popularność do zaawansowanych funkcji zorientowanych obiektowo, które obsługują zestaw i ich ogólnego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="fb1e8-107">Klas podstawowych i klasy abstrakcyjne są specjalne grupy logiczne, dotyczące rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="fb1e8-108">Interfejsy są typy, które może być implementowany przez typy odwołań i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="fb1e8-109">Ten sposób mogą one służyć jako elementy główne w hierarchii polimorficzne typy odwołań i typów wartości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="fb1e8-110">Ponadto interfejsów może służyć do symulacji wielokrotnego dziedziczenia, która nie jest natywnie obsługiwane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="fb1e8-111">Struktury są generalnie w przypadku typów wartości i powinna być zarezerwowana dla małych, prostych typów, podobne do elementów podstawowych języka.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="fb1e8-112">Typy wyliczeniowe są w wyjątkowym przypadku okna typy wartości używane do definiowania krótkie zestawy wartości, takich jak dni tygodnia, kolory konsoli i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="fb1e8-113">Klasy statyczne są typy, które mają być kontenery dla statycznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="fb1e8-114">Często służą one do zapewnienia skróty do innych operacji.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="fb1e8-115">Delegatów, wyjątki, atrybuty, tablice i kolekcje są wszystkie przypadki specjalne typy odwołań, przeznaczone dla konkretnych zastosowań i wytyczne dotyczące ich projektów i użycia są omówione w innym miejscu w tym podręczniku.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="fb1e8-116">**✓ DO** upewnij się, że każdy typ jest dobrze zdefiniowany zestaw elementów członkowskich powiązane, nie tylko losowe kolekcji funkcji niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb1e8-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fb1e8-117">In This Section</span></span>  
 [<span data-ttu-id="fb1e8-118">Wybieranie między klasą i strukturą</span><span class="sxs-lookup"><span data-stu-id="fb1e8-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="fb1e8-119">Projekt klasy abstrakcyjnej</span><span class="sxs-lookup"><span data-stu-id="fb1e8-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="fb1e8-120">Projekt klasy statycznej</span><span class="sxs-lookup"><span data-stu-id="fb1e8-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="fb1e8-121">Projekt interfejsu</span><span class="sxs-lookup"><span data-stu-id="fb1e8-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="fb1e8-122">Projekt struktury</span><span class="sxs-lookup"><span data-stu-id="fb1e8-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="fb1e8-123">Projekt wyliczeń</span><span class="sxs-lookup"><span data-stu-id="fb1e8-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="fb1e8-124">Zagnieżdżone typy</span><span class="sxs-lookup"><span data-stu-id="fb1e8-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="fb1e8-125">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="fb1e8-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fb1e8-126">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="fb1e8-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1e8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb1e8-127">See also</span></span>

- [<span data-ttu-id="fb1e8-128">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="fb1e8-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

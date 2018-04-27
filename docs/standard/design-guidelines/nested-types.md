---
title: Zagnieżdżone typy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 681e11ef3994e4c38dee9f99c6c82cc4b103a0db
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="nested-types"></a><span data-ttu-id="15e72-102">Zagnieżdżone typy</span><span class="sxs-lookup"><span data-stu-id="15e72-102">Nested Types</span></span>
<span data-ttu-id="15e72-103">Zagnieżdżony typ jest typ zdefiniowany w zakresie innego typu, która jest wywoływana typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="15e72-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="15e72-104">Zagnieżdżony typ ma dostęp do wszystkich elementów członkowskich jego typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="15e72-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="15e72-105">Na przykład ma dostęp do prywatnego pól zdefiniowane w typie otaczającym i chronione pola zdefiniowane w wszystkich nadrzędnych typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="15e72-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="15e72-106">Ogólnie rzecz biorąc zagnieżdżone typy powinny być używane rzadko.</span><span class="sxs-lookup"><span data-stu-id="15e72-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="15e72-107">Istnieje kilka powodów.</span><span class="sxs-lookup"><span data-stu-id="15e72-107">There are several reasons for this.</span></span> <span data-ttu-id="15e72-108">Niektórzy deweloperzy nie są w pełni zapoznać się z pojęciem.</span><span class="sxs-lookup"><span data-stu-id="15e72-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="15e72-109">Te deweloperzy mogą na przykład wystąpić problemy z składni deklarowania zmiennych w zagnieżdżonych typów.</span><span class="sxs-lookup"><span data-stu-id="15e72-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="15e72-110">Zagnieżdżone typy są również bardzo ściśle powiązane z ich typu otaczającego i jako takie nie są odpowiednie jako typów ogólnego przeznaczenia.</span><span class="sxs-lookup"><span data-stu-id="15e72-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="15e72-111">Zagnieżdżone typy są najbardziej odpowiednie dla modelowania szczegóły implementacji ich typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="15e72-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="15e72-112">Użytkownik końcowy powinna rzadko muszą przeciążać Zadeklaruj zmienne typu zagnieżdżonego i prawie nigdy nie powinien mieć można jawnie utworzyć wystąpienia typów zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="15e72-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="15e72-113">Na przykład moduł wyliczający kolekcji może być zagnieżdżony typ tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="15e72-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="15e72-114">Moduły wyliczające wystąpienia są zazwyczaj tworzone przez ich typu otaczającego i ponieważ instrukcji foreach obsługuje wiele języków, zmienne modułu wyliczającego rzadko muszą być deklarowana przez użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="15e72-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="15e72-115">**CZY ✓** używać zagnieżdżonych typów w przypadku relacji między typu zagnieżdżonego i jej typu zewnętrznego taki sposób, że dostępność elementu członkowskiego semantyka pożądane.</span><span class="sxs-lookup"><span data-stu-id="15e72-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="15e72-116">**X nie** Użyj publicznego typów zagnieżdżonych jako logiczne grupowanie skonstruować; Użyj przestrzeni nazw dla tego.</span><span class="sxs-lookup"><span data-stu-id="15e72-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="15e72-117">**X należy UNIKAĆ** publicznie udostępnione typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="15e72-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="15e72-118">Jedynym wyjątkiem jest zmienne typu zagnieżdżonego muszą być deklarowane tylko w rzadkich scenariuszy, takich jak tworzenie podklas lub innych scenariuszy zaawansowanego dostosowania.</span><span class="sxs-lookup"><span data-stu-id="15e72-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="15e72-119">**X nie** Użyj zagnieżdżone typy, jeśli typ może odwoływać się poza typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="15e72-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="15e72-120">Na przykład wyliczenia przekazany do metody zdefiniowanej dla klasy, nie powinien być zdefiniowany jako typu zagnieżdżonego w klasie.</span><span class="sxs-lookup"><span data-stu-id="15e72-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="15e72-121">**X nie** używać zagnieżdżonych typów, jeśli muszą zostać utworzone przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="15e72-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="15e72-122">Jeśli typ ma konstruktora publicznego, prawdopodobnie nie powinien być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="15e72-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="15e72-123">Jeśli można utworzyć wystąpienia typu, który wydaje się, że wskazuje typ ma miejsce w ramach samodzielnie (można go utworzyć, z którą go, zniszczyć bez kiedykolwiek przy użyciu typu zewnętrznego) i dlatego nie powinny być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="15e72-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="15e72-124">Typy wewnętrzne nie powinna być powszechnie używana poza typu zewnętrznego bez żadnej z relacji jakiejkolwiek do typu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="15e72-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="15e72-125">**X nie** zagnieżdżony typ jako element członkowski interfejsu.</span><span class="sxs-lookup"><span data-stu-id="15e72-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="15e72-126">Wiele języków nie obsługują takich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="15e72-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="15e72-127">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="15e72-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="15e72-128">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="15e72-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e72-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15e72-129">See Also</span></span>  
 [<span data-ttu-id="15e72-130">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="15e72-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="15e72-131">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="15e72-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

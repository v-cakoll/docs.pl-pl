---
title: "Wytyczne dotyczące projektowania Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a812207fb58e6c87c263966081060d02f8038963
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="cf8ac-102">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="cf8ac-102">Framework Design Guidelines</span></span>
<span data-ttu-id="cf8ac-103">Ta sekcja zawiera wskazówki dotyczące projektowania biblioteki, w których rozszerzanie i interakcję z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="cf8ac-104">Celem jest pomoc projektantów biblioteki zapewnienia spójności interfejsu API i łatwość użycia przez zapewnienie ujednolicony model programowania, który jest niezależny od języka programowania, używany do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="cf8ac-105">Zaleca się przestrzegać następujących wytycznych projektowych, podczas tworzenia klasy i składników, które rozszerzają programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="cf8ac-106">Projekt biblioteki niespójne niekorzystnie wpływa na wydajność deweloperów i odradza przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="cf8ac-107">Wytyczne dzielą się na prosty zalecenia prefiksem warunki `Do`, `Consider`, `Avoid`, i `Do not`.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="cf8ac-108">Te wytyczne mają ułatwić zrozumienie kompromis między różnymi rozwiązaniami projektantów biblioteki klasy.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="cf8ac-109">Mogą wystąpić sytuacje, w którym dobrej biblioteki projektu wymaga naruszanie ich tych zaleceń dotyczących projektowania.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="cf8ac-110">Takiej sytuacji należy rzadkich i jest ważne, czy masz przejrzyste i istotne Przyczyna decyzji.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="cf8ac-111">Niniejsze wytyczne pochodzą z książki *Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2*, Krzysztof Cwalina i Abrams Brada.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf8ac-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cf8ac-112">In This Section</span></span>  
 [<span data-ttu-id="cf8ac-113">Zasady nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="cf8ac-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="cf8ac-114">Zawiera wskazówki dotyczące nazewnictwa zestawy, obszary nazw, typy i elementy członkowskie w bibliotekach klas.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="cf8ac-115">Wytyczne dotyczące projektowania typu</span><span class="sxs-lookup"><span data-stu-id="cf8ac-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="cf8ac-116">Wskazówki dotyczące używania statycznych i abstrakcyjnej klasy, interfejsy, wyliczenia, struktur i innych typów.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="cf8ac-117">Wytyczne dotyczące projektowania elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="cf8ac-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="cf8ac-118">Wskazówki dotyczące projektowania i przy użyciu właściwości, metody konstruktorów, pola, zdarzenia, Operatorzy i parametry.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="cf8ac-119">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="cf8ac-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="cf8ac-120">Rozszerzalność funkcjom, takim jak podklasy, za pomocą zdarzeń, wirtualne elementy członkowskie i wywołania zwrotne i opisano sposób wybierania mechanizmy, które najlepiej spełnia wymagania dotyczące sieci w ramach.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="cf8ac-121">Wskazówek dotyczących wyjątków</span><span class="sxs-lookup"><span data-stu-id="cf8ac-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="cf8ac-122">W tym artykule opisano wskazówek dotyczących projektowania, wyrzucanie i połowowe wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="cf8ac-123">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="cf8ac-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="cf8ac-124">W tym artykule opisano wskazówki dotyczące przy użyciu popularne typy tablic, atrybuty i kolekcje, obsługi serializacji i przeładowanie operatorów równości.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="cf8ac-125">Wspólne wzorce projektowe</span><span class="sxs-lookup"><span data-stu-id="cf8ac-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="cf8ac-126">Zawiera wskazówki dotyczące wybierania i wdrażanie właściwości zależności i wzorzec dispose.</span><span class="sxs-lookup"><span data-stu-id="cf8ac-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="cf8ac-127">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="cf8ac-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cf8ac-128">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="cf8ac-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8ac-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf8ac-129">See Also</span></span>  
 [<span data-ttu-id="cf8ac-130">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cf8ac-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="cf8ac-131">Plan dla środowiska .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cf8ac-131">Roadmap for the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [<span data-ttu-id="cf8ac-132">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="cf8ac-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)

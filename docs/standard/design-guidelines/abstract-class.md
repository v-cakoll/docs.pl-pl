---
title: Projekt klasy abstrakcyjnej
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 739f86acd534549bc997dc7a939cf43a0c6fc3cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="cc44d-102">Projekt klasy abstrakcyjnej</span><span class="sxs-lookup"><span data-stu-id="cc44d-102">Abstract Class Design</span></span>
<span data-ttu-id="cc44d-103">**X nie** zdefiniuj public lub protected wewnętrzny konstruktorów w typach abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="cc44d-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="cc44d-104">Konstruktory powinny być publiczne, tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="cc44d-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="cc44d-105">Ponieważ nie można utworzyć wystąpienia typu abstrakcyjnego, typ ogólny z publicznym konstruktorem jest niepoprawnie zaprojektowany i mylące dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cc44d-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="cc44d-106">**CZY ✓** Definiowanie chronionych lub wewnętrzny konstruktora w klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="cc44d-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="cc44d-107">Konstruktor chroniony jest najczęściej i po prostu umożliwia klasy podstawowej w celu własną inicjowania podczas tworzenia podtypów.</span><span class="sxs-lookup"><span data-stu-id="cc44d-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="cc44d-108">Wewnętrzny Konstruktor może służyć do ograniczania konkretnych implementacji klasy abstrakcyjnej do zestawu Definiowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="cc44d-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="cc44d-109">**CZY ✓** Podaj co najmniej jednego typu konkretnego, która dziedziczy po każdej klasy abstrakcyjnej, którą można wysłać.</span><span class="sxs-lookup"><span data-stu-id="cc44d-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="cc44d-110">Wykonywanie dzięki temu można sprawdzić poprawności projektu klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="cc44d-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="cc44d-111">Na przykład <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją <xref:System.IO.Stream?displayProperty=nameWithType> klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="cc44d-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="cc44d-112">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="cc44d-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cc44d-113">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="cc44d-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc44d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc44d-114">See Also</span></span>  
 [<span data-ttu-id="cc44d-115">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="cc44d-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="cc44d-116">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="cc44d-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

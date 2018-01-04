---
title: "Klasy podstawowe stosowania obiektów abstrakcyjnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96264456ac6afc569c46caf5faed6c37ea22bc8e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="be2f9-102">Klasy podstawowe stosowania obiektów abstrakcyjnych</span><span class="sxs-lookup"><span data-stu-id="be2f9-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="be2f9-103">Mówiąc ściślej klasa staje się klasę podstawową, gdy inna klasa pochodzi od niego.</span><span class="sxs-lookup"><span data-stu-id="be2f9-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="be2f9-104">Na potrzeby tej sekcji jednak klasa podstawowa jest przeznaczone głównie do zapewnienia wspólnej abstrakcji lub innych klas do ponownego użycia niektórych Domyślna implementacja jednak dziedziczenia klasy.</span><span class="sxs-lookup"><span data-stu-id="be2f9-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="be2f9-105">Klasy podstawowe zwykle sit trakcie hierarchii dziedziczenia między abstrakcję elementu głównego hierarchii i kilka implementacji niestandardowych u dołu.</span><span class="sxs-lookup"><span data-stu-id="be2f9-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>  
  
 <span data-ttu-id="be2f9-106">Służą one jako obiekty pomocnicze implementacji wykonywania obiektów abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="be2f9-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="be2f9-107">Na przykład, jeden z obiektów abstrakcyjnych struktury uporządkowanej kolekcji elementów jest <xref:System.Collections.Generic.IList%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="be2f9-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="be2f9-108">Implementowanie <xref:System.Collections.Generic.IList%601> nie jest prosta, i w związku z tym Framework zapewnia kilka klas podstawowych, takich jak <xref:System.Collections.ObjectModel.Collection%601> i <xref:System.Collections.ObjectModel.KeyedCollection%602>, służące jako pomocników wykonywania kolekcje niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="be2f9-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>  
  
 <span data-ttu-id="be2f9-109">Klasy podstawowe zwykle nie są dostosowane do służyć jako obiekty abstrakcyjne samodzielnie, ponieważ mogą one zawierać zbyt wiele implementacji.</span><span class="sxs-lookup"><span data-stu-id="be2f9-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="be2f9-110">Na przykład `Collection<T>` klasa podstawowa zawiera wiele implementacji związane z faktu, że implementuje nongeneric `IList` interfejsu (w celu lepszej integracji z kolekcjami nierodzajowe) i na fakt, że jest ona kolekcję elementów są przechowywane w pamięć w jednym z jego pól.</span><span class="sxs-lookup"><span data-stu-id="be2f9-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>  
  
 <span data-ttu-id="be2f9-111">Jak już wspomniano klasy podstawowe zapewniają cenne pomocy dla użytkowników, którzy muszą implementować obiektów abstrakcyjnych, ale w tym samym czasie może być istotne odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="be2f9-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="be2f9-112">One Dodaj powierzchni i zwiększyć głębokość hierarchii dziedziczenia i dlatego koncepcyjnie skomplikować platformę.</span><span class="sxs-lookup"><span data-stu-id="be2f9-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="be2f9-113">W związku z tym klas podstawowej należy używać tylko wtedy, gdy zawierają wartość użytkownikom platformy.</span><span class="sxs-lookup"><span data-stu-id="be2f9-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="be2f9-114">Jeśli zawierają wartość tylko do obiektów implementujących RAM, w którym wielkość delegowania do wewnętrznej implementacji zamiast dziedziczenia z klasy podstawowej należy uznać należy unikać ich.</span><span class="sxs-lookup"><span data-stu-id="be2f9-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>  
  
 <span data-ttu-id="be2f9-115">**ROZWAŻ ✓** wprowadzania base klasy abstrakcyjny, nawet jeśli nie zawierają żadnych abstrakcyjne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="be2f9-115">**✓ CONSIDER** making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="be2f9-116">To wyraźnie komunikuje się dla użytkowników, że klasa jest przeznaczona wyłącznie do być dziedziczone z.</span><span class="sxs-lookup"><span data-stu-id="be2f9-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>  
  
 <span data-ttu-id="be2f9-117">**ROZWAŻ ✓** umieszczenie w oddzielnych nazw typów połączeniach scenariusz klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="be2f9-117">**✓ CONSIDER** placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="be2f9-118">Zgodnie z definicją klasy podstawowe są przeznaczone do rozszerzalności zaawansowanych scenariuszy i w związku z tym nie są interesujące większości użytkowników.</span><span class="sxs-lookup"><span data-stu-id="be2f9-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>  
  
 <span data-ttu-id="be2f9-119">**X należy UNIKAĆ** nazw klas podstawowych z sufiksem "Podstawowy", jeśli klasa jest przeznaczona do użycia w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="be2f9-119">**X AVOID** naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>  
  
 <span data-ttu-id="be2f9-120">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="be2f9-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="be2f9-121">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="be2f9-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2f9-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be2f9-122">See Also</span></span>  
 [<span data-ttu-id="be2f9-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="be2f9-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="be2f9-124">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="be2f9-124">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

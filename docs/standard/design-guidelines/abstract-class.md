---
title: Projekt klasy abstrakcyjnej
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: KrzysztofCwalina
ms.openlocfilehash: 6eec3bb4575b89c6476e6c3410050c705141777f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550418"
---
# <a name="abstract-class-design"></a><span data-ttu-id="6dc9d-102">Projekt klasy abstrakcyjnej</span><span class="sxs-lookup"><span data-stu-id="6dc9d-102">Abstract Class Design</span></span>
<span data-ttu-id="6dc9d-103">**X DO NOT** zdefiniuj public lub protected wewnętrzny konstruktorów w typach abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="6dc9d-104">Konstruktory powinny być publiczne, tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia tego typu.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="6dc9d-105">Ponieważ nie można utworzyć wystąpienia typu abstrakcyjnego, typ ogólny z publicznym konstruktorem jest niepoprawnie zaprojektowany i może być mylące dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="6dc9d-106">**✓ DO** Definiowanie chronionych lub wewnętrzny konstruktora w klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="6dc9d-107">Konstruktor chroniony jest częściej używana i po prostu umożliwia klasy bazowej o postępowaniu swój własny inicjowania podtypów są tworzone.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="6dc9d-108">Konstruktor wewnętrznej może służyć do ograniczenia konkretnych implementacji klasy abstrakcyjnej do zestawu, Definiowanie klasy.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="6dc9d-109">**✓ DO** Podaj co najmniej jednego typu konkretnego, która dziedziczy po każdej klasy abstrakcyjnej, którą można wysłać.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="6dc9d-110">Wykonując pozwala sprawdzić projekt klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="6dc9d-111">Na przykład <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją <xref:System.IO.Stream?displayProperty=nameWithType> klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="6dc9d-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="6dc9d-112">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="6dc9d-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6dc9d-113">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="6dc9d-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc9d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dc9d-114">See also</span></span>

- [<span data-ttu-id="6dc9d-115">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="6dc9d-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="6dc9d-116">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="6dc9d-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

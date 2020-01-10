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
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709598"
---
# <a name="abstract-class-design"></a><span data-ttu-id="90142-102">Projekt klasy abstrakcyjnej</span><span class="sxs-lookup"><span data-stu-id="90142-102">Abstract Class Design</span></span>
<span data-ttu-id="90142-103">**X DO NOT** zdefiniuj public lub protected wewnętrzny konstruktorów w typach abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="90142-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="90142-104">Konstruktory powinny być publiczne tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="90142-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="90142-105">Ponieważ nie można tworzyć wystąpień typu abstrakcyjnego, typ abstrakcyjny z konstruktorem publicznym jest niepoprawnie zaprojektowany i mylący dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="90142-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="90142-106">**✓ DO** Definiowanie chronionych lub wewnętrzny konstruktora w klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="90142-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="90142-107">Chroniony Konstruktor jest bardziej powszechny, a po prostu pozwala klasie bazowej na wykonywanie własnej inicjalizacji podczas tworzenia podtypów.</span><span class="sxs-lookup"><span data-stu-id="90142-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="90142-108">Wewnętrzny Konstruktor może służyć do ograniczania konkretnych implementacji klasy abstrakcyjnej do zestawu definiującego klasę.</span><span class="sxs-lookup"><span data-stu-id="90142-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="90142-109">**✓ DO** Podaj co najmniej jednego typu konkretnego, która dziedziczy po każdej klasy abstrakcyjnej, którą można wysłać.</span><span class="sxs-lookup"><span data-stu-id="90142-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="90142-110">Dzięki temu można sprawdzić poprawność projektu klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="90142-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="90142-111">Na przykład <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją klasy abstrakcyjnej <xref:System.IO.Stream?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90142-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="90142-112">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="90142-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="90142-113">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="90142-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90142-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90142-114">See also</span></span>

- [<span data-ttu-id="90142-115">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="90142-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="90142-116">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="90142-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

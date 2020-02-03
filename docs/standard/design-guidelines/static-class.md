---
title: Projekt klasy statycznej
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743597"
---
# <a name="static-class-design"></a><span data-ttu-id="1ae66-102">Projekt klasy statycznej</span><span class="sxs-lookup"><span data-stu-id="1ae66-102">Static Class Design</span></span>
<span data-ttu-id="1ae66-103">Klasa statyczna jest definiowana jako Klasa, która zawiera tylko statyczne elementy członkowskie (oczywiście oprócz członków wystąpienia dziedziczonych z <xref:System.Object?displayProperty=nameWithType> i ewentualnie konstruktora prywatnego).</span><span class="sxs-lookup"><span data-stu-id="1ae66-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="1ae66-104">Niektóre języki zapewniają wbudowaną obsługę klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="1ae66-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="1ae66-105">W C# 2,0 i nowszych, gdy Klasa jest zadeklarowana jako statyczna, jest zapieczętowana, abstrakcyjna i nie można zastępować ani deklarować elementów członkowskich wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ae66-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="1ae66-106">Klasy statyczne są kompromisem między czystym i prostotą zorientowanym na obiektem.</span><span class="sxs-lookup"><span data-stu-id="1ae66-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="1ae66-107">Są one często używane do udostępniania skrótów do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType>), posiadaczy metod rozszerzających lub funkcji, dla których pełna otoka zorientowana obiektowo jest nieuzasadniona (na przykład <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="1ae66-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="1ae66-108">✔️ używać klas statycznych oszczędnie.</span><span class="sxs-lookup"><span data-stu-id="1ae66-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="1ae66-109">Klasy statyczne powinny być używane tylko jako klasy pomocnicze dla rdzenia zorientowanego obiektowo struktury.</span><span class="sxs-lookup"><span data-stu-id="1ae66-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="1ae66-110">❌ nie Traktuj klas statycznych jako zasobników dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="1ae66-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="1ae66-111">❌ nie deklaruj ani nie przesłonić składowych wystąpienia w klasach statycznych.</span><span class="sxs-lookup"><span data-stu-id="1ae66-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="1ae66-112">✔️ NALEŻY zadeklarować klasy statyczne jako zapieczętowane, abstrakcyjne i dodać konstruktora wystąpienia prywatnego, jeśli język programowania nie ma wbudowanej obsługi dla klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="1ae66-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="1ae66-113">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="1ae66-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1ae66-114">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="1ae66-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1ae66-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ae66-115">See also</span></span>

- [<span data-ttu-id="1ae66-116">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1ae66-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="1ae66-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1ae66-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

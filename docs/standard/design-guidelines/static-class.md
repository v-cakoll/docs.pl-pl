---
title: Projekt klasy statycznej
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192735"
---
# <a name="static-class-design"></a><span data-ttu-id="e716d-102">Projekt klasy statycznej</span><span class="sxs-lookup"><span data-stu-id="e716d-102">Static Class Design</span></span>
<span data-ttu-id="e716d-103">Klasa statyczna jest zdefiniowany jako klasę, która zawiera tylko statyczne elementy członkowskie (oczywiście oprócz składowych wystąpienia dziedziczonych po elemencie <xref:System.Object?displayProperty=nameWithType> i prawdopodobnie Konstruktor prywatny).</span><span class="sxs-lookup"><span data-stu-id="e716d-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="e716d-104">Niektóre języki zapewniają obsługę wbudowanych klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="e716d-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="e716d-105">W języku C# w wersji 2.0 i nowszych wersjach gdy klasa jest zadeklarowany jako statyczny, jest zapieczętowany, abstract, a nie składowych wystąpienia mogą zostać zastąpione lub zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="e716d-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="e716d-106">Klasy statyczne są kompromis między czystego programowania obiektowego i prostota.</span><span class="sxs-lookup"><span data-stu-id="e716d-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="e716d-107">Często są one używane do zapewnienia skróty do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType>), posiadaczy metody rozszerzenia lub funkcji, dla którego jest nieuzasadnione otokę pełnej zorientowane obiektowo (takie jak <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="e716d-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="e716d-108">**✓ DO** oszczędnie używać klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="e716d-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="e716d-109">Klasy statyczne powinna służyć tylko jako klasy pomocnicze dla core zorientowane obiektowo Framework.</span><span class="sxs-lookup"><span data-stu-id="e716d-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="e716d-110">**X DO NOT** Traktuj klas statycznych jako różne zasobnika.</span><span class="sxs-lookup"><span data-stu-id="e716d-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="e716d-111">**X DO NOT** zadeklarować lub zastąpienie elementów członkowskich wystąpienia w klasie statycznej.</span><span class="sxs-lookup"><span data-stu-id="e716d-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="e716d-112">**✓ DO** zadeklarować klas statycznych jako sealed, abstrakcyjny i dodać Konstruktor prywatny wystąpienia, jeśli język programowania nie ma wbudowaną obsługę klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="e716d-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="e716d-113">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="e716d-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e716d-114">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="e716d-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e716d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e716d-115">See also</span></span>

- [<span data-ttu-id="e716d-116">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="e716d-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="e716d-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="e716d-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

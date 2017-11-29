---
title: Projekt klasy statyczne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28fe3756a2881e8f746616f8275b505b1a01eada
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="static-class-design"></a><span data-ttu-id="0222f-102">Projekt klasy statyczne</span><span class="sxs-lookup"><span data-stu-id="0222f-102">Static Class Design</span></span>
<span data-ttu-id="0222f-103">Klasa statyczna jest zdefiniowany jako klasa, która zawiera tylko elementy członkowskie static (oczywiście oprócz elementów członkowskich wystąpień odziedziczone <xref:System.Object?displayProperty=nameWithType> i prawdopodobnie Konstruktor prywatny).</span><span class="sxs-lookup"><span data-stu-id="0222f-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="0222f-104">W przypadku niektórych języków zapewniają obsługę wbudowanych klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="0222f-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="0222f-105">W języku C# 2.0 lub nowszy po klasie został zadeklarowany jako statyczny, jest zapieczętowany, abstrakcyjny i żadnych członków wystąpienia można zastąpić lub zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="0222f-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="0222f-106">Klasy statyczne są kompromis między czystym obiektowego i prostota.</span><span class="sxs-lookup"><span data-stu-id="0222f-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="0222f-107">Często są one używane do zapewnienia skróty do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType>), posiadaczy metody rozszerzenia lub funkcji, dla którego jest nieuzasadnione otoka pełnej zorientowane obiektowo (takie jak <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0222f-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="0222f-108">**CZY ✓** oszczędnie używać klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="0222f-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="0222f-109">Klasy statyczne należy używać tylko jako klasy pomocnicze dla core zorientowane obiektowo platformy.</span><span class="sxs-lookup"><span data-stu-id="0222f-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="0222f-110">**X nie** Traktuj klas statycznych jako różne zasobnika.</span><span class="sxs-lookup"><span data-stu-id="0222f-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="0222f-111">**X nie** zadeklarować lub zastąpienie elementów członkowskich wystąpienia w klasie statycznej.</span><span class="sxs-lookup"><span data-stu-id="0222f-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="0222f-112">**CZY ✓** zadeklarować klas statycznych jako sealed, abstrakcyjny i dodać Konstruktor prywatny wystąpienia, jeśli język programowania nie ma wbudowaną obsługę klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="0222f-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="0222f-113">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="0222f-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0222f-114">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="0222f-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0222f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0222f-115">See Also</span></span>  
 [<span data-ttu-id="0222f-116">Wytyczne dotyczące projektowania typu</span><span class="sxs-lookup"><span data-stu-id="0222f-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="0222f-117">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="0222f-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

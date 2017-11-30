---
title: "Modyfikatory dostępu (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="3d977-102">Modyfikatory dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3d977-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="3d977-103">Modyfikatory dostępu są używany do określenia dostępności zadeklarowany element członkowski lub typ słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="3d977-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="3d977-104">W tej sekcji przedstawiono Modyfikatory cztery dostępu:</span><span class="sxs-lookup"><span data-stu-id="3d977-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="3d977-105">publiczny</span><span class="sxs-lookup"><span data-stu-id="3d977-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="3d977-106">chronione</span><span class="sxs-lookup"><span data-stu-id="3d977-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="3d977-107">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="3d977-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="3d977-108">prywatne</span><span class="sxs-lookup"><span data-stu-id="3d977-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="3d977-109">Można określić następujące sześć poziomów ułatwień dostępu, używając modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="3d977-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="3d977-110">`public`: Dostępu nie jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="3d977-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="3d977-111">`protected`: Dostęp jest ograniczony do zawierający klasy lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="3d977-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="3d977-112">`internal`: Dostęp jest ograniczony do bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3d977-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="3d977-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Dostęp jest ograniczony do bieżącego zestawu lub typy pochodzące od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="3d977-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="3d977-114">`private`: Dostęp jest ograniczony do typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="3d977-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="3d977-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Dostęp jest ograniczony do zawierającego klasę lub typy pochodzące od klasy zawierające w bieżącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="3d977-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="3d977-116">W tej sekcji przedstawiono również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3d977-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="3d977-117">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md): za pomocą modyfikatorów dostępu cztery Aby zadeklarować sześciu poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="3d977-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="3d977-118">[Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md): Określa, gdzie w sekcjach program elementem członkowskim można odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="3d977-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="3d977-119">[Ograniczenia dotyczące poziomów ułatwień dostępu przy użyciu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Podsumowanie ograniczenia dotyczące używania zadeklarowany poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="3d977-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d977-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d977-120">See Also</span></span>  
 [<span data-ttu-id="3d977-121">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3d977-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3d977-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3d977-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d977-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3d977-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3d977-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="3d977-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="3d977-125">Słowa kluczowe dostępu</span><span class="sxs-lookup"><span data-stu-id="3d977-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="3d977-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="3d977-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
